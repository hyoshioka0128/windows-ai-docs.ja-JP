---
title: Windows Machine Learning for Desktop (C++) チュートリアル
description: このチュートリアルでは、デスクトップ向けの単純な Windows ML アプリケーションを構築する方法を示します。
ms.date: 5/10/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 619a0c39b824abc2ed2eaee1ca8f95f95a4aa9c7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157666"
---
# <a name="tutorial-create-a-windows-machine-learning-desktop-application-c"></a>チュートリアル:Windows Machine Learning デスクトップアプリケーションを作成するC++()

Windows ML Api は、デスクトップ (Win32) アプリケーション内C++の機械学習モデルと簡単に対話するために利用できます。 アプリケーションの読み込み、バインド、評価の3つの手順を使用すると、機械学習の機能を活用できます。

![負荷 -> バインド -> 評価](../images/load-bind-evaluate.png)

ここでは、 [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp)で入手できる SqueezeNet オブジェクト検出サンプルの少し簡略化されたバージョンを作成します。 完了したときの動作を確認するには、完全なサンプルをダウンロードできます。

ここでは、 C++Winml api にアクセスするために/WinRT を使用します。 詳細については、「 [ C++WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) 」を参照してください。

このチュートリアルでは、次の方法について説明します。

> [!div class="checklist"]
> * 機械学習モデルを読み込む
> * 画像を[Videoframe](https://docs.microsoft.com/uwp/api/windows.media.videoframe)として読み込む
> * モデルの入力と出力をバインドする
> * モデルを評価し、意味のある結果を出力する

## <a name="prerequisites"></a>前提条件

* [Visual Studio 2019](https://developer.microsoft.com/windows/downloads)(または Visual Studio 2017、バージョン15.7.4 以降)
* [Windows 10 バージョン1809以降](https://www.microsoft.com/software-download/windows10)
* [Windows SDK、ビルド17763以降](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK
)
* /WinRT 用C++Visual Studio 拡張機能
    1. Visual Studio で、[**ツール] [> の拡張機能と更新プログラム**] を選択します。
    2. 左側のウィンドウで **[オンライン]** を選択し、右側の検索ボックスを使用して "WinRT" を検索します。
    3. **[ C++/WinRT]** を選択し、 **[ダウンロード]** をクリックして、Visual Studio を閉じます。
    4. インストール手順に従って、Visual Studio を再度開きます。
* [Windows-Machine Learning Github リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)(ZIP ファイルとしてダウンロードするか、コンピューターに複製することができます)

## <a name="create-the-project"></a>プロジェクトの作成

まず、Visual Studio でプロジェクトを作成します。

1. **[ファイル > 新しい > プロジェクト]** を選択して、 **[新しいプロジェクト]** ウィンドウを開きます。
2. 左側のウィンドウで、 **[インストール済み > C++ Visual > windows デスクトップ]** を選択し、中央にある **[windowsC++コンソールアプリケーション (/WinRT)]** を選択します。
3. プロジェクトに**名前**と**場所**を指定し、[ **OK]** をクリックします。
4. **[新しいユニバーサル Windows プラットフォームプロジェクト]** ウィンドウで、**ターゲット**と**最小バージョン**の両方をビルド17763以降に設定し、 **[OK]** をクリックします。
5. コンピューターのアーキテクチャに応じて、上部のツールバーのドロップダウンメニューが [ **デバッグ**] に設定されていることを確認します。
6. Ctrl キーを押し**ながら F5**キーを押して、デバッグを行わずにプログラムを実行します。 ターミナルは、"Hello world" というテキストを使用して開く必要があります。 任意のキーを押して閉じます。

## <a name="load-the-model"></a>モデルの読み込み

次に、LearningModel を使用して、ONNX モデルをプログラムに読み込みます[。](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath)

1. **.Pch** (**ヘッダーファイル**フォルダー内) に次`include`のステートメントを追加します (これらは、必要なすべての api へのアクセスを提供します)。
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

2. [**メイン .cpp** (**ソースファイル**] フォルダー内) で、次`using`のステートメントを追加します。
    ```cpp
    using namespace Windows::AI::MachineLearning;
    using namespace Windows::Foundation::Collections;
    using namespace Windows::Graphics::Imaging;
    using namespace Windows::Media;
    using namespace Windows::Storage;

    using namespace std;
    ```

3. ステートメントの`using`後に、次の変数宣言を追加します。
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

4. 次の事前宣言をグローバル変数の後に追加します。
    ```cpp
    // Forward declarations
    void LoadModel();
    VideoFrame LoadImageFile(hstring filePath);
    void BindModel();
    void EvaluateModel();
    void PrintResults(IVectorView<float> results);
    void LoadLabels();
    ```

5. **メイン .cpp**で、"Hello world" コード (の後`main` `init_apartment`に関数内のすべてのもの) を削除します。
6. SqueezeNet リポジトリのローカル複製内の**onnx**ファイルを見つけます **()** 。 ある必要があります **\Windows-Machine-Learning\SharedContent\models** します。
7. ファイルパスをコピーし、先頭で定義`modelPath`した変数に割り当てます。 文字列`L`をワイド文字列にして、で`hstring`適切に動作するようにし、バックスラッシュを追加して円記号 (`\`) をエスケープすることを忘れないでください。 以下に例を示します。
    ```cpp
    hstring modelPath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\models\\SqueezeNet.onnx";
    ```

8. まず、メソッドを`LoadModel`実装します。 メソッドの`main`後に次のメソッドを追加します。 このメソッドは、モデルを読み込み、かかった時間を出力します。
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

9. 最後に、 `main`メソッドからこのメソッドを呼び出します。
    ```cpp
    LoadModel();
    ```

10. デバッグせずにプログラムを実行します。 モデルが正常に読み込まれたことがわかります。

## <a name="load-the-image"></a>イメージを読み込む

次に、このプログラムにイメージファイルを読み込みます。

1. 次のメソッドを追加します。 このメソッドは、指定されたパスからイメージを読み込み、そこから[Videoframe](https://docs.microsoft.com/uwp/api/windows.media.videoframe)を作成します。
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

2. メソッドで、 `main`このメソッドの呼び出しを追加します。
    ```cpp
    imageFrame = LoadImageFile(imagePath);
    ```

3. **Windows Machine Learning**リポジトリのローカル複製内の**メディア**フォルダーを探します。 配置されている必要がある **\Windows-Machine-Learning\SharedContent\media** します。
4. そのフォルダー内のいずれかのイメージを選択し、そのファイルパスを`imagePath`一番上に定義した変数に割り当てます。 ワイド文字列にするには`L` 、にプレフィックスを付け、バックスラッシュを別の円記号でエスケープすることを忘れないでください。 以下に例を示します。
    ```cpp
    hstring imagePath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\media\\kitten_224.png";
    ```

5. デバッグなしでプログラムを実行します。 イメージが正常に読み込まれたことがわかります。

## <a name="bind-the-input-and-output"></a>入力と出力をバインドする

次に、モデルに基づいてセッションを作成し、 [LearningModelBinding](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind)を使用してセッションからの入力と出力をバインドします。 バインディングの詳細については、「[モデルのバインド](bind-a-model.md)」を参照してください。

1. `BindModel` メソッドを実装します。 これにより、モデルとデバイス、およびそのセッションに基づくバインドに基づいてセッションが作成されます。 次に、その名前を使用して、作成した変数に入力と出力をバインドします。 入力機能に "data_0" という名前が付けられ、出力機能の名前が "softmaxout_1" であることが事前にわかっています。 これらのプロパティは、オンラインモデルの視覚化ツールである[Netron](https://lutzroeder.github.io/Netron/)で開くことで、任意のモデルに対して表示できます。
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

2. メソッドからへ`BindModel`の呼び出しを追加します。 `main`
    ```cpp
    BindModel();
    ```

3. デバッグなしでプログラムを実行します。 モデルの入力と出力は、正常にバインドされている必要があります。 少しで完了です。

## <a name="evaluate-the-model"></a>モデルを評価する

ここでは、このチュートリアルの最初の図の最後の手順であるを**評価**します。 LearningModelSession を使用してモデルを評価し[ます。](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate)

1. `EvaluateModel` メソッドを実装します。 このメソッドは、セッションを取得し、バインドと相関 ID を使用してそれを評価します。 相関 ID は、後で使用して、特定の評価呼び出しを出力結果に一致させることができるものです。 ここでも、出力の名前が "softmaxout_1" であることが事前にわかっています。
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

2. 次に、を`PrintResults`実装してみましょう。 このメソッドは、イメージに含まれる可能性があるオブジェクトの上位3つの確率を取得し、それらを出力します。
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

3. また、を実装`LoadLabels`する必要もあります。 このメソッドは、モデルが認識できるすべての異なるオブジェクトを含むラベルファイルを開き、解析します。
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

4. **Windows Machine Learning**リポジトリのローカル複製で、 **Labels**ファイルを見つけます。 必要がある **\Windows-Machine-Learning\Samples\SqueezeNetObjectDetection\Desktop\cpp** します。
5. このファイルパスを、先頭`labelsFilePath`で定義した変数に割り当てます。 バックスラッシュは、必ず別の円記号でエスケープしてください。 以下に例を示します。
    ```cpp
    string labelsFilePath = "C:\\Repos\\Windows-Machine-Learning\\Samples\\SqueezeNetObjectDetection\\Desktop\\cpp\\Labels.txt";
    ```

6. `EvaluateModel`メソッドにの呼び出しを追加します。 `main`
    ```cpp
    EvaluateModel();
    ```

7. デバッグなしでプログラムを実行します。 これで、画像の内容が正しく認識されるようになりました。 出力される内容の例を次に示します。
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

## <a name="next-steps"></a>次の手順

バンザイは、 C++デスクトップアプリケーションでオブジェクト検出を実行しています。 次に、コマンドライン引数を使用して、モデルファイルとイメージファイルをハードコーディングせずに入力してみてください。 GitHub のサンプルと同様です。 また、GPU などの別のデバイスで評価を実行して、パフォーマンスの違いを確認することもできます。

GitHub で他のサンプルを試してみてください。

## <a name="see-also"></a>関連項目

* [Windows ML のサンプル (GitHub)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)
* [Windows. AI. 名前空間](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Windows ML](index.md)

[!INCLUDE [help](../includes/get-help.md)]
