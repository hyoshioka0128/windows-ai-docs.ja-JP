---
title: デスクトップ向け Windows Machine Learning (C++) チュートリアル
description: このチュートリアルでは、デスクトップ向けの単純な Windows ML アプリケーションを構築する方法を示します。
ms.date: 5/10/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 619a0c39b824abc2ed2eaee1ca8f95f95a4aa9c7
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70157666"
---
# <a name="tutorial-create-a-windows-machine-learning-desktop-application-c"></a>チュートリアル: Windows Machine Learning デスクトップ アプリケーション (C++) の作成

Windows ML API を利用して、C++ デスクトップ (Win32) アプリケーション内で、機械学習モデルを簡単に操作できます。 読み込み、バインド、評価の 3 つの手順を使用すると、アプリケーションで機械学習の機能を活用できます。

![読み込み -> バインド -> 評価](../images/load-bind-evaluate.png)

[GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp) で入手できる SqueezeNet オブジェクト検出のサンプルを少し簡略化したバージョンを作成します。 完了したときにそれがどのようになるかを確認する場合は、完全なサンプルをダウンロードできます。

C++/WinRT を使用して、WinML API にアクセスします。 詳細については、「[C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)」を参照してください。

このチュートリアルでは、次の方法について説明します。

> [!div class="checklist"]
> * 機械学習モデルを読み込む
> * [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe) として画像を読み込む
> * モデルの入力と出力をバインドする
> * モデルを評価し、意味のある結果を出力する

## <a name="prerequisites"></a>前提条件

* [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (または Visual Studio 2017 バージョン 15.7.4 以降)
* [Windows 10 バージョン 1809 以降](https://www.microsoft.com/software-download/windows10)
* [Windows SDK ビルド 17763 以降](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK
)
* C++/WinRT 用 Visual Studio 拡張機能
    1. Visual Studio で、 **[ツール] > [拡張機能と更新プログラム]** を選択します。
    2. 左ウィンドウで **[オンライン]** を選択し、右側の検索ボックスを使用して "WinRT" を検索します。
    3. **[C++/WinRT]** を選択し、 **[ダウンロード]** をクリックして、Visual Studio を閉じます。
    4. インストール手順に従って、Visual Studio を再度開きます。
* [Windows-Machine-Learning Github リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning) (ZIP ファイルとしてダウンロードするか、またはコンピューターに複製できます)

## <a name="create-the-project"></a>プロジェクトの作成

まず、Visual Studio でプロジェクトを作成します。

1. **[ファイル] > [新規作成] > [プロジェクト]** の順に選択し、 **[新しいプロジェクト]** ウィンドウを開きます。
2. 左ウィンドウで、 **[インストール済み] > [Visual C++] > [Windows デスクトップ]** を選択し、中央にある **[Windows コンソール アプリケーション (C++/WinRT)]** を選択します。
3. プロジェクトに**名前**と**場所**を指定し、 **[OK]** をクリックします。
4. **[新しいユニバーサル Windows プラットフォーム プロジェクト]** ウィンドウで、 **[ターゲット]** と **[最小バージョン]** の両方をビルド 17763 以降に設定し、 **[OK]** をクリックします。
5. 上部のツールバーのドロップダウン メニューが、コンピューターのアーキテクチャに応じて、 **[デバッグ]** および **[x64]** または **[x86]** に設定されていることを確認します。
6. **Ctrl + F5** キーを押して、デバッグなしでプログラムを実行します。 ターミナルが開き、"Hello world" などのテキストが表示されます。 任意のキーを押して閉じます。

## <a name="load-the-model"></a>モデルを読み込む

次に、[LearningModel LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath) を使用して、ONNX モデルをプログラムに読み込みます。

1. **pch.h** (**ヘッダー ファイル** フォルダー内) に、次の `include` ステートメントを追加します (これらにより、必要なすべての API にアクセスできるようになります)。
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

2. **main.cpp** (**ソース ファイル** フォルダー内) に、次の `using` ステートメントを追加します。
    ```cpp
    using namespace Windows::AI::MachineLearning;
    using namespace Windows::Foundation::Collections;
    using namespace Windows::Graphics::Imaging;
    using namespace Windows::Media;
    using namespace Windows::Storage;

    using namespace std;
    ```

3. `using` ステートメントの後に、次の変数宣言を追加します。
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

5. **main.cpp** で、"Hello world" コード (`init_apartment` の後の `main` 関数内のすべて) を削除します。
6. **Windows-Machine-Learning** リポジトリのローカルの複製で、**SqueezeNet.onnx** ファイルを見つけます。 これは **\Windows-Machine-Learning\SharedContent\models** にあります。
7. ファイル パスをコピーし、上部に定義した `modelPath` 変数にそれを割り当てます。 `hstring` で正常に動作するように、文字列に `L` のプレフィックスを付けてワイド文字列にし、円記号を追加して円記号 (`\`) をエスケープしてください。 たとえば、次のように入力します。
    ```cpp
    hstring modelPath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\models\\SqueezeNet.onnx";
    ```

8. まず、`LoadModel` メソッドを実装します。 `main` メソッドの後に次のメソッドを追加します。 このメソッドは、モデルを読み込み、かかった時間を出力します。
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

9. 最後に、`main` メソッドからこのメソッドを呼び出します。
    ```cpp
    LoadModel();
    ```

10. デバッグなしでプログラムを実行します。 モデルが正常に読み込まれたことが表示されます。

## <a name="load-the-image"></a>画像を読み込む

次に、このプログラムに画像ファイルを読み込みます。

1. 次のメソッドを追加します。 このメソッドは、指定されたパスから画像を読み込み、そこから [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe) を作成します。
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

2. `main` メソッドで、このメソッドの呼び出しを追加します。
    ```cpp
    imageFrame = LoadImageFile(imagePath);
    ```

3. **Windows-Machine-Learning** リポジトリのローカルの複製で、**media** フォルダーを見つけます。 これは **\Windows-Machine-Learning\SharedContent\media** にあります。
4. そのフォルダー内のいずれかの画像を選択し、上部に定義した `imagePath` 変数にそのファイル パスを割り当てます。 それに `L` のプレフィックスを付けてワイド文字列にし、円記号にもう 1 つ円記号を付けてエスケープしてください。 たとえば、次のように入力します。
    ```cpp
    hstring imagePath = L"C:\\Repos\\Windows-Machine-Learning\\SharedContent\\media\\kitten_224.png";
    ```

5. デバッグなしでプログラムを実行します。 画像が正常に読み込まれたことが表示されます。

## <a name="bind-the-input-and-output"></a>入力と出力をバインドする

次に、モデルに基づいてセッションを作成し、[LearningModelBinding.Bind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind) を使用してセッションからの入力と出力をバインドします。 バインドの詳細については、「[モデルを作成する](bind-a-model.md)」を参照してください。

1. `BindModel` メソッドを実装します。 これにより、モデルとデバイスに基づいてセッションが作成され、そのセッションに基づいてバインドが作成されます。 次に、入力と出力を、それらの名前を使用して作成した変数にバインドします。 入力特徴には "data_0" という名前が付けられ、出力特徴には "softmaxout_1" という名前が付けられていることが事前にわかっています。 モデルのこれらのプロパティは、オンラインのモデル視覚化ツールの [Netron](https://lutzroeder.github.io/Netron/) で開くことで確認できます。
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

2. `main` メソッドから `BindModel` の呼び出しを追加します。
    ```cpp
    BindModel();
    ```

3. デバッグなしでプログラムを実行します。 モデルの入力と出力が、正常にバインドされます。 もう少しで完了です。

## <a name="evaluate-the-model"></a>モデルを評価する

これで、このチュートリアルの冒頭にある図の最後の手順である**評価**に到達しました。 [LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate) を使用してモデルを評価します。

1. `EvaluateModel` メソッドを実装します。 このメソッドは、セッションを取得し、バインドと関連付け ID を使用してそれを評価します。 関連付け ID は、後で使用して、特定の評価呼び出しを出力結果と照合できるようにするものです。 ここでも、出力の名前が "softmaxout_1" であることが事前にわかっています。
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

2. 次に、`PrintResults` を実装します。 このメソッドは、画像に含まれている可能性があるオブジェクトの上位 3 つを取得し、それらを出力します。
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

3. さらに `LoadLabels` を実装する必要もあります。 このメソッドは、モデルが認識できるすべての異なるオブジェクトを含むラベル ファイルを開き、解析します。
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

4. **Windows-Machine-Learning** リポジトリのローカルの複製で、**Labels.txt** ファイルを見つけます。 これは **\Windows-Machine-Learning\Samples\SqueezeNetObjectDetection\Desktop\cpp** にあります。
5. このファイル パスを、上部に定義した `labelsFilePath` 変数に割り当てます。 円記号にもう 1 つ円記号を付けてエスケープしてください。 たとえば、次のように入力します。
    ```cpp
    string labelsFilePath = "C:\\Repos\\Windows-Machine-Learning\\Samples\\SqueezeNetObjectDetection\\Desktop\\cpp\\Labels.txt";
    ```

6. `main` メソッドに `EvaluateModel` の呼び出しを追加します。
    ```cpp
    EvaluateModel();
    ```

7. デバッグなしでプログラムを実行します。 これで、画像の内容が正しく認識されるようになります。 出力される可能性のある内容の例を次に示します。
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

C++ デスクトップ アプリケーションで物体検出が機能するようになりました。 次に、GitHub のサンプルで行っているのと同様に、モデル ファイルと画像ファイルをハードコーディングせずに、コマンド ライン引数を使用して、それらを入力してみることができます。 さらに、GPU などの別のデバイスで評価を実行して、パフォーマンスの違いを確認することもできます。

GitHub の他のサンプルを試して、お好きなように拡張してみてください。

## <a name="see-also"></a>関連項目

* [Windows ML のサンプル (GitHub)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)
* [Windows.AI.MachineLearning 名前空間](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [Windows ML](index.md)

[!INCLUDE [help](../includes/get-help.md)]
