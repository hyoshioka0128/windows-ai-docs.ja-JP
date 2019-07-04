---
author: eliotcowley
title: デスクトップの Windows Machine Learning (C++) チュートリアル
description: このチュートリアルでは、デスクトップの単純な Windows ML アプリケーションを構築する方法を示します。
ms.author: elcowle
ms.date: 5/10/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 084b9254f8a22bd9163c5494943bc1b48559c9ee
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182014"
---
# <a name="tutorial-create-a-windows-machine-learning-desktop-application-c"></a>チュートリアル:Windows Machine Learning のデスクトップ アプリケーションの作成 (C++)

Windows ML Api を活用すると、内での機械学習モデルを簡単にやり取りC++デスクトップ (Win32) アプリケーションです。 読み込み、バインド、および評価の 3 つの手順を使用して、アプリケーションは、機械学習の力を利用できます。

![負荷 -> バインド -> 評価](../images/load-bind-evaluate.png)

利用できる SqueezeNet オブジェクト検出のサンプルの少し簡略化されたバージョンを作成しました[GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp)します。 どうなるかのように完了したときに表示する場合は、完全なサンプルをダウンロードできます。

使用するC++/WinRT WinML Api にアクセスします。 参照してください[ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)詳細についてはします。

このチュートリアルで学習する方法。

> [!div class="checklist"]
> * 機械学習モデルを読み込む
> * としてイメージを読み込む、 [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe)
> * モデルの入力と出力をバインドします。
> * モデルを評価して、意味のある結果の印刷

## <a name="prerequisites"></a>前提条件

* [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (または Visual Studio 2017 バージョン 15.7.4 またはそれ以降)
* [Windows 10、1809 またはそれ以降のバージョン](https://www.microsoft.com/software-download/windows10)
* [Windows SDK、17763 またはそれ以降のビルド](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK
)
* 用の visual Studio 拡張機能C++/WinRT
    1. Visual Studio で、次のように選択します。**ツール > 拡張機能と更新**します。
    2. 選択**オンライン**左側と右側の検索ボックスを使用して"WinRT"を検索します。
    3. 選択 **C++/WinRT**、 をクリックして**ダウンロード**、Visual Studio を閉じます。
    4. 次のインストール手順についてから、再び Visual Studio を開きます。
* [Windows-Machine Learning の Github リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)(かとしてダウンロードできますが、ZIP または複製をコンピューターに)

## <a name="create-the-project"></a>プロジェクトの作成

まず、Visual Studio でプロジェクトを作成します。

1. 選択**ファイル > 新規 > プロジェクト**を開く、**新しいプロジェクト**ウィンドウ。
2. 左側のウィンドウで次のように選択します。**インストール済み > Visual C++ > Windows デスクトップ**、し、真ん中の次のように選択します。 **Windows コンソール アプリケーション (C++/WinRT)** します。
3. プロジェクトを与える、**名前**と**場所**、順にクリックします **[ok]** 。
4. **新しいユニバーサル Windows プラットフォーム プロジェクト**ウィンドウで、設定、**ターゲット**と**最小バージョン**17763 以降のビルドとクリックの両方**OK**.
5. 必ず上部のツールバーのドロップダウン メニューに設定されます**デバッグ**、どちらか**x64**または**x86**コンピューターのアーキテクチャによって異なります。
6. キーを押して**Ctrl + F5**デバッグなしでプログラムを実行します。 "Hello world"テキストでターミナルを開く必要があります。 閉じるには任意のキーを押します。

## <a name="load-the-model"></a>モデルを読み込む

次に、ONNX モデルを使用して、プログラムをロードしましょう[LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath):

1. **Pch.h** (で、**ヘッダー ファイル**フォルダー)、次の追加`include`ステートメント (これら私たちにアクセスできるように、すべての Api にも、必要があります)。
    ```cpp
    #include <winrt/Windows.AI.MachineLearning.h>
    #include <winrt/Windows.Foundation.Collections.h>
    #include <winrt/Windows.Graphics.Imaging.h>
    #include <winrt/Windows.Media.h>
    #include <winrt/Windows.Storage.h>

    #include <string>
    #include <fstream>

    #include <Windows.h>
    ```

2. **Main.cpp** (で、**ソースファイル**フォルダー)、次の追加`using`ステートメント。
    ```cpp
    using namespace Windows::AI::MachineLearning;
    using namespace Windows::Foundation::Collections;
    using namespace Windows::Graphics::Imaging;
    using namespace Windows::Media;
    using namespace Windows::Storage;

    using namespace std;
    ```

3. 後に次の変数宣言を追加、`using`ステートメント。
    ```cpp
    // Global variables
    hstring modelPath;
    string deviceName = "default";
    hstring imagePath;
    LearningModel model = nullptr;
    LearningModelDeviceKind deviceKind = LearningModelDeviceKind::Default;
    LearningModelSession session = nullptr;
    LearningModelBinding binding = nullptr;
    VideoFrame imageFrame = nullptr;
    string labelsFilePath;
    vector<string> labels;
    ```

4. グローバル変数の後に、次の事前宣言を追加します。
    ```cpp
    // Forward declarations
    void LoadModel();
    VideoFrame LoadImageFile(hstring filePath);
    void BindModel();
    void EvaluateModel();
    void PrintResults(IVectorView<float> results);
    void LoadLabels();
    ```

5. **Main.cpp**、"Hello world"のコードを削除 (内のすべて、`main`後関数`init_apartment`)。
6. 検索、 **SqueezeNet.onnx**ファイルのローカル複製で、 **Windows Machine Learning**リポジトリ。 ある必要があります **\Windows-Machine-Learning\SharedContent\models** します。
7. ファイルのパスをコピーし、それを割り当てる、`modelPath`上部にある定義した場所の変数。 文字列をプレフィックスに注意してください、`L`ようにし、ワイド文字の文字列を正常に動作する`hstring`、円記号をエスケープして (`\`) 追加の円記号で。 例:
    ```cpp
    hstring modelPath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\models\\SqueezeNet.onnx";
    ```

8. 最初に、実装、`LoadModel`メソッド。 後は、次のメソッドを追加、`main`メソッド。 このメソッドは、モデルを読み込みにかかる時間を出力します。
    ```cpp
    void LoadModel()
    {
        // load the model
        printf("Loading modelfile '%ws' on the '%s' device\n", modelPath.c_str(), deviceName.c_str());
        DWORD ticks = GetTickCount();
        model = LearningModel::LoadFromFilePath(modelPath);
        ticks = GetTickCount() - ticks;
        printf("model file loaded in %d ticks\n", ticks);
    }
    ```

9. 最後からこのメソッドを呼び出して、`main`メソッド。
    ```cpp
    LoadModel();
    ```

10. デバッグを行わず、プログラムを実行します。 モデルが正常に読み込まれることがわかります。

## <a name="load-the-image"></a>イメージを読み込み

次に、イメージ ファイルを読み込みプログラムに。

1. 次のメソッドを追加します。 このメソッドは、指定されたパスからイメージの読み込みし、作成、 [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe)から。
    ```cpp
    VideoFrame LoadImageFile(hstring filePath)
    {
        printf("Loading the image...\n");
        DWORD ticks = GetTickCount();
        VideoFrame inputImage = nullptr;

        try
        {
            // open the file
            StorageFile file = StorageFile::GetFileFromPathAsync(filePath).get();
            // get a stream on it
            auto stream = file.OpenAsync(FileAccessMode::Read).get();
            // Create the decoder from the stream
            BitmapDecoder decoder = BitmapDecoder::CreateAsync(stream).get();
            // get the bitmap
            SoftwareBitmap softwareBitmap = decoder.GetSoftwareBitmapAsync().get();
            // load a videoframe from it
            inputImage = VideoFrame::CreateWithSoftwareBitmap(softwareBitmap);
        }
        catch (...)
        {
            printf("failed to load the image file, make sure you are using fully qualified paths\r\n");
            exit(EXIT_FAILURE);
        }

        ticks = GetTickCount() - ticks;
        printf("image file loaded in %d ticks\n", ticks);
        // all done
        return inputImage;
    }
    ```

2. 呼び出しでこのメソッドを追加、`main`メソッド。
    ```cpp
    imageFrame = LoadImageFile(imagePath);
    ```

3. 検索、**メディア**フォルダーのローカル複製で、 **Windows Machine Learning**リポジトリ。 配置されている必要がある **\Windows-Machine-Learning\SharedContent\media** します。
4. 、そのフォルダー内のイメージを選択し、へのファイル パスを割り当てます、`imagePath`上部にある定義した場所の変数。 前にプレフィックスに注意してください、`L`ワイド文字の文字列を別の円記号の円記号をエスケープするとします。 次に、例を示します。
    ```cpp
    hstring imagePath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\media\\kitten_224.png";
    ```

5. デバッグを行わず、プログラムを実行します。 正常に読み込まれたイメージが表示されます。

## <a name="bind-the-input-and-output"></a>入力と出力をバインドします。

次に、モデルに基づいてセッションを作成し、入力と出力を使用して、セッションからバインド[LearningModelBinding.Bind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind)します。 バインディングの詳細については、次を参照してください。[モデル バインド](bind-a-model.md)します。

1. 実装、`BindModel`メソッド。 これは、モデルと、デバイスに基づいてセッションとセッション ベースのバインディングを作成します。 バインドして、入力と出力変数の名前を使用して作成しました。 "Data_0"という名前の入力機能が前もって知るためし、"softmaxout_1"という名前の出力の機能です。 開くことによって、モデルのこれらのプロパティを確認できます[Netron](https://lutzroeder.github.io/Netron/)、オンラインのモデルの視覚化ツール。
    ```cpp
    void BindModel()
    {
        printf("Binding the model...\n");
        DWORD ticks = GetTickCount();

        // now create a session and binding
        session = LearningModelSession{ model, LearningModelDevice(deviceKind) };
        binding = LearningModelBinding{ session };
        // bind the intput image
        binding.Bind(L"data_0", ImageFeatureValue::CreateFromVideoFrame(imageFrame));
        // bind the output
        vector<int64_t> shape({ 1, 1000, 1, 1 });
        binding.Bind(L"softmaxout_1", TensorFloat::Create(shape));

        ticks = GetTickCount() - ticks;
        printf("Model bound in %d ticks\n", ticks);
    }
    ```

2. 呼び出しを追加して`BindModel`から、`main`メソッド。
    ```cpp
    BindModel();
    ```

3. デバッグを行わず、プログラムを実行します。 モデルの入力と出力が正常にバインドする必要があります。 私たちはもう少しです。

## <a name="evaluate-the-model"></a>モデルを評価します。

今回の図は、最後の手順のこのチュートリアルでは、先頭に**Evaluate**します。 使用して、モデルを評価しますが[LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate):

1. 実装、`EvaluateModel`メソッド。 このメソッドが、セッションに受け取り、バインドとの関連付け ID を使用して評価 関連付け ID は、結果を出力する特定の評価の呼び出しが一致するように後で使用できます可能性があります。 ここでも、出力の名前が"softmaxout_1"前もってわかっています。
    ```cpp
    void EvaluateModel()
    {
        // now run the model
        printf("Running the model...\n");
        DWORD ticks = GetTickCount();

        auto results = session.Evaluate(binding, L"RunId");

        ticks = GetTickCount() - ticks;
        printf("model run took %d ticks\n", ticks);

        // get the output
        auto resultTensor = results.Outputs().Lookup(L"softmaxout_1").as<TensorFloat>();
        auto resultVector = resultTensor.GetAsVectorView();
        PrintResults(resultVector);
    }
    ```

2. 今すぐ実装してみましょう`PrintResults`します。 このメソッドにどのようなオブジェクトが、イメージでは、上位 3 つの確率を取得し、それに出力します。
    ```cpp
    void PrintResults(IVectorView<float> results)
    {
        // load the labels
        LoadLabels();
        // Find the top 3 probabilities
        vector<float> topProbabilities(3);
        vector<int> topProbabilityLabelIndexes(3);
        // SqueezeNet returns a list of 1000 options, with probabilities for each, loop through all
        for (uint32_t i = 0; i < results.Size(); i++)
        {
            // is it one of the top 3?
            for (int j = 0; j < 3; j++)
            {
                if (results.GetAt(i) > topProbabilities[j])
                {
                    topProbabilityLabelIndexes[j] = i;
                    topProbabilities[j] = results.GetAt(i);
                    break;
                }
            }
        }
        // Display the result
        for (int i = 0; i < 3; i++)
        {
            printf("%s with confidence of %f\n", labels[topProbabilityLabelIndexes[i]].c_str(), topProbabilities[i]);
        }
    }
    ```

3. 実装する必要もあります`LoadLabels`します。 このメソッドは、すべてのモデルが認識できるし、解析は、さまざまなオブジェクトを含むラベル ファイルを開きます。
    ```cpp
    void LoadLabels()
    {
        // Parse labels from labels file.  We know the file's entries are already sorted in order.
        ifstream labelFile{ labelsFilePath, ifstream::in };
        if (labelFile.fail())
        {
            printf("failed to load the %s file.  Make sure it exists in the same folder as the app\r\n", labelsFilePath.c_str());
            exit(EXIT_FAILURE);
        }

        std::string s;
        while (std::getline(labelFile, s, ','))
        {
            int labelValue = atoi(s.c_str());
            if (labelValue >= labels.size())
            {
                labels.resize(labelValue + 1);
            }
            std::getline(labelFile, s);
            labels[labelValue] = s;
        }
    }
    ```

4. 検索、 **Labels.txt**ファイルのローカル複製で、 **Windows Machine Learning**リポジトリ。 必要がある **\Windows-Machine-Learning\Samples\SqueezeNetObjectDetection\Desktop\cpp** します。
5. このファイルのパスに割り当てる、`labelsFilePath`上部にある定義した場所の変数。 もう 1 つの円記号の円記号をエスケープしてください。 例:
    ```cpp
    string labelsFilePath = "C:\\Repos\\Windows-Machine-Learning\\Samples\\SqueezeNetObjectDetection\\Desktop\\cpp\\Labels.txt";
    ```

6. 呼び出しを追加して`EvaluateModel`で、`main`メソッド。
    ```cpp
    EvaluateModel();
    ```
    
7. デバッグを行わず、プログラムを実行します。 今すぐ正しくが認識されますイメージに含まれる内容! その出力がありますの例を次に示します。
    ```sh
    Loading modelfile 'C:\Repos\Windows-Machine-Learning\SharedContent\models\SqueezeNet.onnx' on the 'default' device
    model file loaded in 250 ticks
    Loading the image...
    image file loaded in 78 ticks
    Binding the model...Model bound in 15 ticks
    Running the model...
    model run took 16 ticks
    tabby, tabby cat with confidence of 0.931461
    Egyptian cat with confidence of 0.065307
    Persian cat with confidence of 0.000193
    ```

## <a name="next-steps"></a>次のステップ

誕生日おめでとう、したオブジェクトの検出での作業をC++デスクトップ アプリケーションです。 次に、ハードコーディングするはどのような GitHub のサンプルと似ていますではなく、モデルおよびイメージ ファイルを入力するコマンドライン引数を使用してもかまいません。 GPU のパフォーマンスがどのように異なるかを確認するように、別のデバイスで評価を実行してもよい。

GitHub の他のサンプルをいろいろし、それらを拡張することです。

## <a name="see-also"></a>関連項目

* [Windows の ML サンプル (GitHub)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)
* [Windows.AI.MachineLearning Namespace](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Windows ML](index.md)

[!INCLUDE [help](../includes/get-help.md)]
