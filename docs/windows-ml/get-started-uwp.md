---
title: Windows Machine Learning UWP アプリケーションを作成するC#()
description: このステップ バイ ステップ チュートリアルを使って、Windows ML で初めての UWP アプリケーションを作成します。
ms.date: 5/10/2019
ms.topic: article
keywords: Windows 10, UWP, Windows Machine Learning, WinML, Windows ML
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4a8e46835b0018a8057c1056c6dd59b9589b0f9c
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156740"
---
# <a name="tutorial-create-a-windows-machine-learning-uwp-application-c"></a>チュートリアル:Windows Machine Learning UWP アプリケーションを作成するC#()

このチュートリアルでは、トレーニング済みの機械学習モデルを使用して、ユーザーによって描画された数字を認識する単純なユニバーサル Windows プラットフォームアプリケーションを作成します。 このチュートリアルでは、主に UWP アプリケーションで Windows ML を読み込んで使用する方法について説明します。

次のビデオでは、このチュートリアルの基になっているサンプルについて説明します。

<br/>

> [!VIDEO https://www.youtube.com/embed/yC3HKAv0aj4]

完成したチュートリアルのコードを見たい場合は、 [Winml GitHub リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cs)で確認できます。 [ C++/Cx](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cppcx)でも使用できます。

## <a name="prerequisites"></a>前提条件

- Windows 10 (バージョン1809以降)
- [Windows 10 SDK](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)(ビルド17763以降)
- [Visual Studio 2019](https://developer.microsoft.com/windows/downloads)(または Visual Studio 2017、バージョン15.7.4 以降)
- [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2)または[2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)用の Windows Machine Learning コードジェネレーター拡張機能
- いくつかの基本的C#な UWP と知識

## <a name="1-open-the-project-in-visual-studio"></a>1. Visual Studio でプロジェクトを開く

Visual Studio を起動し、開くプロジェクト GitHub からダウンロードすると後、 **MNIST_Demo.sln** ファイル (である必要がある **&lt;リポジトリへのパス&gt;\Windows-Machine-Learning\Samples\MNIST\Tutorial\cs**)。 ソリューションが使用不可と表示されている場合は、**ソリューションエクスプローラー**でプロジェクトを右クリックし、 **[プロジェクトの再読み込み]** をクリックする必要があります。

次のような XAML コントロールとイベントを実装したテンプレートが用意されています。

- 数字を描画するための [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)。
- 数字の解釈とキャンバスの消去を行う[ボタン](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button)。
- **System.windows.controls.inkcanvas>** の出力を[videoframe](https://docs.microsoft.com/uwp/api/windows.media.videoframe)に変換するヘルパールーチン。

**ソリューションエクスプローラー**内のプロジェクトには、次の3つの主要なコードファイルがあります。

- **Mainpage.xaml** -すべての xaml コードを使用して、 **system.windows.controls.inkcanvas>** 、ボタン、およびラベルの UI を作成します。
- **MainPage.xaml.cs** -アプリケーションコードが存在する場所です。
- **Helper.cs** -イメージ形式をトリミングおよび変換するヘルパールーチン。

![Visual Studio のソリューション エクスプローラーとプロジェクト ファイル](../images/get-started1.png)

## <a name="2-build-and-run-the-project"></a>2. プロジェクトをビルドして実行する

Visual Studio のツールバーで、**ソリューションプラットフォーム**を **[x64]** に変更して、デバイスが64ビットの場合はローカルコンピューターでプロジェクトを実行し、32ビットの場合は **[x86]** に変更します。 (Windows 設定アプリをチェックインできます。システム **> > デバイスの仕様 > システムの種類に関する情報**)。

プロジェクトを実行するには、ツールバーの **[デバッグの開始]** ボタンをクリックするか、 **F5**キーを押します。 アプリケーションでは、ユーザーが数字を記述できる**system.windows.controls.inkcanvas>** 、数値を解釈するための**認識**ボタン、解釈された数字がテキストとして表示される空のラベルフィールド、および消去するため **の明確な数字ボタンを表示する必要があります。System.windows.controls.inkcanvas>** 。

![アプリケーションのスクリーンショット](../images/get-started2.png)

> [!NOTE]
> プロジェクトがビルドされない場合は、プロジェクトの配置ターゲットバージョンの変更が必要になることがあります。 **ソリューションエクスプローラー**でプロジェクトを右クリックし、 **[プロパティ]** を選択します。 **[アプリケーション]** タブで、OS と SDK に一致する**ターゲットバージョン**と**最小バージョン**を設定します。

> [!NOTE]
> アプリケーションが既にインストールされていることを示す警告が表示された場合は、 **[はい]** を選択して展開を続行します。 まだ動作しない場合は、Visual Studio を閉じて再度開く必要があります。

## <a name="3-download-a-model"></a>3.モデルのダウンロード

次に、アプリケーションに追加する機械学習モデルを取得しましょう。 このチュートリアルでは、 [Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/)を使用してトレーニングし、 [ONNX 形式にエクスポート](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb)した事前トレーニング済みの mnist モデルを使用します。

MNIST モデルは既に**Assets**フォルダーに含まれており、既存のアイテムとしてアプリケーションに追加する必要があります。 また、GitHub の [ONNX Model Zoo](https://github.com/onnx/models) から事前トレーニング済みのモデルをダウンロードすることもできます。

## <a name="4-add-the-model"></a>4。モデルの追加

**ソリューションエクスプローラー**で **[Assets]** フォルダーを右クリックし、[**既存項目**の**追加** > ] を選択します。 ファイルピッカーで ONNX モデルの場所をポイントし、 **[追加]** をクリックします。

次の 2 つの新しいファイルがプロジェクトに追加されます。

- **onnx** -トレーニング済みのモデル。
- **mnist.cs** -Windows ML で生成されたコード。

![新しいファイルが追加されたソリューション エクスプローラー](../images/get-started3.png)

アプリケーションをコンパイルするときにモデルがビルドされるようにするには、 **onnx**ファイルを右クリックし、 **[プロパティ]** を選択します。 **[ビルド アクション]** で **[コンテンツ]** を選択します。

次に、 **mnist.cs**ファイルで新しく生成されたコードを見てみましょう。 次の 3 つのクラスがあります。

- **mnistModel**は、機械学習モデル表現を作成し、システムの既定のデバイスにセッションを作成し、特定の入力と出力をモデルにバインドし、モデルを非同期的に評価します。
- **mnistInput**モデルで想定される入力の型を初期化します。 この場合、入力には[Imagefeaturevalue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)が必要です。
- **mnistOutput**モデルによって出力される型を初期化します。 この場合、出力は**Plus214_Output_0**と[いう型の一覧になります](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)。

これらのクラスを使って、プロジェクトでモデルを読み込み、バインドし、評価していきます。

## <a name="5-load-bind-and-evaluate-the-model"></a>5。モデルの読み込み、バインド、および評価

Windows ML アプリケーションでは、次のパターンを使用します。読み込み > バインド > 評価します。

1. 機械学習モデルを読み込む。
2. 入力と出力をモデルにバインドする。
3. モデルを評価して結果を確認する。

**Mnist.cs**で生成されたインターフェイスコードを使用して、アプリケーションでモデルを読み込んでバインドし、評価します。

まず、 **MainPage.xaml.cs**でモデル、入力、および出力をインスタンス化してみましょう。 **Mainpage.xaml**クラスに次のメンバー変数を追加します。

```csharp
private mnistModel ModelGen;
private mnistInput ModelInput = new mnistInput();
private mnistOutput ModelOutput;
```

次に、 **Loadmodelasync**でモデルを読み込みます。 このメソッドは、モデルのメソッドを使用する前に呼び出す必要があります (つまり、 **mainpage.xaml**の[Loaded](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.loaded)イベント、 [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto)オーバーライド、または**recognizeButton_Click**が呼び出される前の任意の場所)。 **MnistModel**クラスは、mnist モデルを表し、システムの既定のデバイスにセッションを作成します。 モデルを読み込むには、 **CreateFromStreamAsync**メソッドを呼び出して、ONNX ファイルをパラメーターとして渡します。

```csharp
private async Task LoadModelAsync()
{
    // Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/mnist.onnx"));
    ModelGen = await mnistModel.CreateFromStreamAsync(modelFile as IRandomAccessStreamReference);
}
```

> [!NOTE]
> **IRandomAccessStreamReference**の下に赤い下線が表示された場合は、名前空間を含める必要があります。 その上にカーソルを置き、 **ctrl +** キーを押します。 ドロップダウンメニューから **[使用]** を選択します。

次に、入力と出力をモデルにバインドします。 生成されたコードには、 **mnistInput**および**mnistOutput**ラッパークラスも含まれています。 **MnistInput**クラスは、モデルの予期される入力を表し、 **mnistOutput**クラスはモデルの予想される出力を表します。

モデルの入力オブジェクトを初期化するには、 **mnistInput**クラスコンストラクターを呼び出し、アプリケーションデータを渡して、入力データがモデルで想定されている入力型と一致していることを確認します。 **MnistInput**クラスは**imagefeaturevalue**を想定しているため、ヘルパーメソッドを使用して、入力の**imagefeaturevalue**を取得します。

**Helper.cs**に含まれているヘルパー関数を使用して、 **system.windows.controls.inkcanvas>** の内容をコピーし、それを**imagefeaturevalue**型に変換して、モデルにバインドします。

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);
}
```

出力については、指定された入力で**Evaluateasync**を呼び出すだけです。 入力が初期化されたら、モデルの**Evaluateasync**メソッドを呼び出して、入力データに対してモデルを評価します。 **Evaluateasync**は、入力と出力をモデルオブジェクトにバインドし、入力に基づいてモデルを評価します。

このモデルでは、出力が返されます。そのため、最初にこれをわかりやすいデータ型に変換し、返されたリストを解析して確率が最も高い数字を特定し、その値を表示します。

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

最後に、 **system.windows.controls.inkcanvas>** をクリアして、ユーザーが別の数値を描画できるようにします。

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="6-launch-the-application"></a>6。アプリケーションを起動する

アプリケーションをビルドして起動すると ( **F5**キーを押すと)、 **system.windows.controls.inkcanvas>** で描画された数値を認識できるようになります。

![アプリケーションの完了](../images/get-started4.png)

これで、初めての Windows ML アプリケーションを作成できました。 Windows ML の使用方法を示すその他のサンプルについては、GitHub の[Windows Machine Learning](https://github.com/Microsoft/Windows-Machine-Learning)リポジトリを参照してください。

[!INCLUDE [help](../includes/get-help.md)]
