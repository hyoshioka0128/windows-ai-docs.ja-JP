---
author: eliotcowley
title: Windows Machine Learning の UWP アプリケーションの作成 (C#)
description: このステップ バイ ステップ チュートリアルでは、Windows の ML を使用した最初の UWP アプリケーションを作成します。
ms.author: elcowle
ms.date: 3/14/2019
ms.topic: article
keywords: Windows 10, UWP, Windows Machine Learning, WinML, Windows ML
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 6110f2e8032a2cd6084306c1e92c1b673e881211
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474449"
---
# <a name="tutorial-create-a-windows-machine-learning-uwp-application-c"></a>チュートリアル:Windows Machine Learning の UWP アプリケーションの作成 (C#)

このチュートリアルでは、ユーザーによって描画される数字を認識するため、トレーニングされた機械学習モデルを使用する単純なユニバーサル Windows プラットフォーム アプリケーションを作成します。 このチュートリアルは、主に読み込み、UWP アプリケーションで Windows ML を使用する方法について説明します。

次のビデオでは、このチュートリアルに基づくサンプル手順について説明します。

<br/>

> [!VIDEO https://www.youtube.com/embed/yC3HKAv0aj4]

単に、完成したチュートリアルのコードを確認する場合で見つけることができます、 [WinML GitHub リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cs)します。 使用できるも[ C++/CX](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cppcx)します。

## <a name="prerequisites"></a>前提条件

- Windows 10 (バージョンは 1809 以降)
- [Windows 10 SDK](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) (ビルド 17763 以降)
- [Visual Studio 2017](https://developer.microsoft.com/windows/downloads)
- [Windows の Machine Learning のコード ジェネレーターの VS 2017 の拡張機能](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
- いくつかの基本的な UWP とC#ナレッジ

## <a name="1-open-the-project-in-visual-studio"></a>1. Visual Studio でプロジェクトを開きます

Visual Studio を起動し、開くプロジェクト GitHub からダウンロードすると後、 **MNIST_Demo.sln**ファイル (である必要がある**&lt;リポジトリへのパス&gt;\Windows-Machine-Learning\Samples\MNIST\Tutorial\cs**)。 ソリューションが利用不可と表示されている場合でプロジェクトを右クリックする必要があります、**ソリューション エクスプ ローラー**選択**プロジェクトの再読み込み**します。

次のような XAML コントロールとイベントを実装したテンプレートが用意されています。

- 数字を描画するための [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)。
- 数字の解釈とキャンバスの消去を行う[ボタン](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button)。
- 変換するヘルパー ルーチン、 **InkCanvas**に出力を[VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe)します。

内で、**ソリューション エクスプ ローラー**プロジェクトに 3 つのメイン コード ファイル。

- **MainPage.xaml** -すべての UI を作成する XAML コードの**InkCanvas**、ボタン、およびラベルを付けます。
- **MainPage.xaml.cs** -、アプリケーション コードが存在します。
- **Helper.cs**のトリミングおよび変換するヘルパー ルーチンのイメージ形式。

![Visual Studio のソリューション エクスプローラーとプロジェクト ファイル](images/get-started1.png)

## <a name="2-build-and-run-the-project"></a>2. ビルドして、プロジェクトの実行

Visual Studio ツールバーで、変更、**ソリューション プラットフォーム**に**x64**デバイスが 64 ビットの場合は、ローカル コンピューターにプロジェクトを実行するまたは**x86** 32 ビットである場合。 (Windows 設定アプリで確認できます。**システム > に関する > デバイスの仕様 > システム型**)。

プロジェクトを実行する をクリックして、**デバッグの開始**  ボタンをツールバー、またはキーを押して**F5**します。 アプリケーションを表示する必要があります、 **InkCanvas**ユーザーは、数字を記述できますが、 **Recognize**数値の解釈にボタン テキスト、および、として解釈される数字が表示される場所を空のラベルフィールド**数字をオフに**をクリアするボタン、 **InkCanvas**します。

![アプリケーションのスクリーンショット](images/get-started2.png)

> [!NOTE]
> プロジェクトがビルドされない場合は、プロジェクトの配置のターゲット バージョンを変更する必要があります。 プロジェクトを右クリックし、**ソリューション エクスプ ローラー**選択**プロパティ**します。 **アプリケーション**タブで、設定、**ターゲット バージョン**と**最小バージョン**OS と SDK の一致するようにします。

> [!NOTE]
> アプリケーションが既にインストールされている警告が発生した場合だけ選択**はい**展開を続行します。 Visual Studio を終了し、それでもうまくいかない場合を再び開く必要があります。

## <a name="3-download-a-model"></a>3.モデルをダウンロードします。

次に、アプリケーションに追加する機械学習モデルを取得します。 このチュートリアルでは、MNIST の事前トレーニング済みモデルでトレーニングされてを使用します、 [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/)と[ONNX 形式にエクスポートされる](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb)します。

MNIST モデルが既に含まれています、**資産** フォルダーは既存の項目として、アプリケーションに追加する必要があります。 また、GitHub の [ONNX Model Zoo](https://github.com/onnx/models) から事前トレーニング済みのモデルをダウンロードすることもできます。

## <a name="4-add-the-model"></a>4。モデルの追加

右クリックして、**資産**フォルダーで、**ソリューション エクスプ ローラー**を選択し、**追加** > **既存項目の**します。 ファイル ピッカーを ONNX モデルの場所をポイントしてクリックして**追加**します。

次の 2 つの新しいファイルがプロジェクトに追加されます。

- **mnist.onnx** -、トレーニングされたモデル。
- **mnist.cs** -The Windows ML によって生成されたコード。

![新しいファイルが追加されたソリューション エクスプローラー](images/get-started3.png)

アプリケーションをコンパイルするときに、モデルを構築することを確認を右クリックして、 **mnist.onnx**ファイル、および選択**プロパティ**します。 **[ビルド アクション]** で **[コンテンツ]** を選択します。

ここで、新しく生成されたコードを見ていきましょう、 **mnist.cs**ファイル。 次の 3 つのクラスがあります。

- **mnistModel**機械学習モデルの表現を作成しますをシステム既定のデバイスにセッションを作成、特定の入力をバインドしますと、モデルに出力し、モデルの評価を非同期にします。 
- **mnistInput**モデルが必要とする入力の種類を初期化します。 この場合、入力が必要ですが、 [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)します。
- **mnistOutput**モデルを出力する型を初期化します。 この場合、出力になりますと呼ばれるリスト**Plus214_Output_0**型の[TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)します。

これらのクラスを使って、プロジェクトでモデルを読み込み、バインドし、評価していきます。

## <a name="5-load-bind-and-evaluate-the-model"></a>5。読み込み、バインド、およびモデルを評価します。

ML の Windows アプリケーション、に従ってするパターンは次のとおりです。ロード > バインド > を評価します。

1. 機械学習モデルを読み込む。
2. 入力と出力をモデルにバインドする。
3. モデルを評価して結果を確認する。

生成されたインターフェイスのコードを使用します**mnist.cs**読み込むをクリックし、バインドして、アプリケーションでは、モデルを評価します。

最初に、 **MainPage.xaml.cs**モデル、入力と出力のインスタンスを作成してみましょう。 次のメンバー変数を追加、 **MainPage**クラス。

```csharp
private mnistModel ModelGen;
private mnistInput ModelInput = new mnistInput();
private mnistOutput ModelOutput;
```

次に、 **LoadModelAsync**モデルをロードしましょう。 モデルのメソッドのいずれかを使用前に、このメソッドを呼び出す必要があります (つまり、 **MainPage**の[Loaded](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.loaded)イベントで、 [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto)上書き、または任意の場所する前に**recognizeButton_Click**と呼びます)。 **MnistModel**クラスは、MNIST モデルを表すし、システムの既定のデバイスにセッションを作成します。 モデルを読み込むには、いわゆる、 **CreateFromStreamAsync**メソッドのパラメーターとして ONNX ファイル。

```csharp
private async Task LoadModelAsync()
{
    // Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/mnist.onnx"));
    ModelGen = await mnistModel.CreateFromStreamAsync(modelFile as IRandomAccessStreamReference);
}
```

> [!NOTE]
> 下の赤い下線が表示された場合**IRandomAccessStreamReference**、その名前空間を含める必要があります。 上にカーソルを置き、キーを押して**Ctrl + です。** 選択と**Windows.Storage.Streams を使用して**ドロップダウン メニューから。

次に、入力と出力をモデルにバインドします。 生成されたコードも含まれています。 **mnistInput**と**mnistOutput**ラッパー クラス。 **MnistInput**クラスは、モデルの必要な入力を表します、 **mnistOutput**クラスは、モデルの予想される出力を表します。

モデルの入力オブジェクトを初期化するために呼び出す、 **mnistInput**クラス コンス トラクター、アプリケーションのデータを渡すと、入力データが、モデルが必要ですが、入力の型と一致するかどうかを確認します。 **MnistInput**クラスが必要ですが、 **ImageFeatureValue**ヘルパー メソッドを使用して取得するため、 **ImageFeatureValue**入力します。

含まれる、ヘルパーを使用して関数の**helper.cs**の内容をコピーします、 **InkCanvas**、型に変換**ImageFeatureValue**、私たちのモデルにバインドします。

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);
}
```

出力では単純に呼び出して**EvaluateAsync**入力に指定します。 入力内容が初期化されると、呼び出し、モデルの**EvaluateAsync**入力データに対してモデルを評価するメソッド。 **EvaluateAsync**入力をバインドおよびモデル オブジェクトへの出力し、入力にモデルを評価します。

モデルは、出力 tensor を返すので、わかりやすいデータ型に変換する最初がどの桁が最も高い確率を特定し、そのいずれかを表示する、返された一覧を解析してされ。

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);

    // Evaluate the model
    ModelOutput = await ModelGen.EvaluateAsync(ModelInput);

    // Convert output to datatype
    IReadOnlyList<float> vectorImage = ModelOutput.Plus214_Output_0.GetAsVectorView();
    IList<float> imageList = vectorImage.ToList();

    // Query to check for highest probability digit
    var maxIndex = imageList.IndexOf(imageList.Max());

    // Display the results
    numberLabel.Text = maxIndex.ToString();
}
```

最後に、私たちを削除する、 **InkCanvas**別の番号を描画するためにユーザーを許可します。

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="6-launch-the-application"></a>6。アプリケーションを起動します。

構築し、アプリケーションを起動 (キーを押して**f5 キーを押して**)、私たちに描画される数を認識するようになります、 **InkCanvas**。

![完全なアプリケーション](images/get-started4.png)

これで初めての Windows の ML アプリケーションを加えた。 Windows の ML を使用する方法を示す他のサンプルをチェック アウト、 [Windows Machine Learning](https://github.com/Microsoft/Windows-Machine-Learning) GitHub のリポジトリ。

[!INCLUDE [help](includes/get-help.md)]
