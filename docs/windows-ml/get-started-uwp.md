---
title: Windows Machine Learning の UWP アプリケーションの作成 (C#)
description: このステップ バイ ステップ チュートリアルを使って、Windows ML で初めての UWP アプリケーションを作成します。
ms.date: 5/10/2019
ms.topic: article
keywords: Windows 10, UWP, Windows Machine Learning, WinML, Windows ML
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4a8e46835b0018a8057c1056c6dd59b9589b0f9c
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156740"
---
# <a name="tutorial-create-a-windows-machine-learning-uwp-application-c"></a>チュートリアル: Windows Machine Learning の UWP アプリケーションの作成 (C#)

このチュートリアルでは、トレーニング済みの機械学習モデルを使ってユーザーが描画した数字を認識する、簡単なユニバーサル Windows プラットフォーム アプリケーションをビルドします。 このチュートリアルでは、UWP アプリケーションで Windows ML を読み込んで使用する方法に主に焦点を当てています。

次のビデオでは、このチュートリアルの基になるサンプルについて説明します。

<br/>

> [!VIDEO https://www.youtube.com/embed/yC3HKAv0aj4]

完了したチュートリアルのコードだけを確認したい場合は、[WinML GitHub リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cs)を参照してください。 [C++/CX](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST/UWP/cppcx) でも利用できます。

## <a name="prerequisites"></a>前提条件

- Windows 10 (バージョン 1809 以降)
- [Windows 10 SDK](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) (ビルド 17763 以降)
- [Visual Studio 2019](https://developer.microsoft.com/windows/downloads) (または Visual Studio 2017 バージョン 15.7.4 以降)
- [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2) または [2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) 用の Windows Machine Learning Code Generator 拡張機能
- UWP と C# のいくつかの基本的な知識

## <a name="1-open-the-project-in-visual-studio"></a>1.Visual Studio でプロジェクトを開く

GitHub からプロジェクトをダウンロードしたら、Visual Studio を起動し、**MNIST_Demo .sln** ファイル ( **&lt;リポジトリのパス&gt;\Windows-Machine-Learning\Samples\MNIST\Tutorial\cs** にあります) を開きます。 ソリューションが利用不可と表示される場合は、**ソリューション エクスプローラー**でプロジェクトを右クリックし、 **[プロジェクトの再読み込み]** を選択する必要があります。

次のような XAML コントロールとイベントを実装したテンプレートが用意されています。

- 数字を描画するための [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas)。
- 数字の解釈とキャンバスの消去を行う[ボタン](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.button)。
- **InkCanvas** の出力を [VideoFram](https://docs.microsoft.com/uwp/api/windows.media.videoframe) に変換するヘルパー ルーチン。

**ソリューション エクスプローラー**内のプロジェクトには、次の 3 つの主なコード ファイルがあります。

- **MainPage.xaml** - **InkCanvas**、ボタン、ラベルの UI を作成する XAML コードがすべて含まれています 。
- **MainPage.xaml.cs** - アプリケーション コードが含まれています。
- **Helper.cs** - トリミングと画像形式の変換を行うヘルパー ルーチンが含まれています。

![Visual Studio のソリューション エクスプローラーとプロジェクト ファイル](../images/get-started1.png)

## <a name="2-build-and-run-the-project"></a>2.プロジェクトをビルドして実行する

Visual Studio のツールバーで、**ソリューション プラットフォーム**を、デバイスが 64 ビットの場合は **x64** に変更して、ローカル コンピューターでプロジェクトを実行するようにし、32 ビットの場合は **x86** に変更します。 (Windows 設定アプリで確認できます。 **[システム] > [バージョン情報] > [デバイスの仕様] > [システムの種類]** )。

プロジェクトを実行するには、ツール バーの **[デバッグの開始]** ボタンをクリックするか、**F5** キーを押します。 アプリケーションには、ユーザーが数字を描画できる **InkCanvas**、数字を解釈する **[Recognize] (認識)** ボタン、解釈された数字がテキストとして表示される空のラベル、**InkCanvas** をクリアする **[Clear Digit] (数字のクリア)** ボタンが表示されます。

![アプリケーションのスクリーンショット](../images/get-started2.png)

> [!NOTE]
> プロジェクトがビルドされない場合は、プロジェクトのデプロイのターゲット バージョンを変更する必要が生じることがあります。 **ソリューション エクスプローラー**でプロジェクトを右クリックし、 **[プロパティ]** を選びます。 **[アプリケーション]** タブで、使用している OS と SDK に合わせて、 **[ターゲット バージョン]** と **[最小バージョン]** を設定します。

> [!NOTE]
> アプリケーションがすでにインストールされていることを示す警告が表示された場合は、 **[はい]** を選択してデプロイを続行します。 まだ動作しない場合は、Visual Studio を閉じて再度開く必要がある場合もあります。

## <a name="3-download-a-model"></a>3.モデルをダウンロードする

次に、アプリケーションに追加する機械学習モデルを入手します。 このチュートリアルでは、[Microsoft Cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/) を使ってトレーニングされ、[ONNX 形式にエクスポートされた](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb)事前トレーニング済みの MNIST モデルを使用します。

MNIST モデルはすでに **Assets** フォルダーに含まれているので、これを既存の項目としてアプリケーションに追加する必要があります。 また、GitHub の [ONNX Model Zoo](https://github.com/onnx/models) から事前トレーニング済みのモデルをダウンロードすることもできます。

## <a name="4-add-the-model"></a>4.モデルの追加

**ソリューション エクスプローラー**で **[Assets]** フォルダーを右クリックし、 **[追加]**  >  **[既存の項目]** を選択します。 ファイル ピッカーで ONNX モデルの場所を参照し、 **[追加]** をクリックします。

次の 2 つの新しいファイルがプロジェクトに追加されます。

- **mnist.onnx** - トレーニング済みのモデル。
- **mnist.cs** - Windows ML で生成されたコード。

![新しいファイルが追加されたソリューション エクスプローラー](../images/get-started3.png)

アプリケーションのコンパイル時にモデルがビルドされるようにするために、**mnist.onnx** ファイルを右クリックし、 **[プロパティ]** を選択します。 **[ビルド アクション]** で **[コンテンツ]** を選択します。

ここで、**mnist.cs** ファイルの新しく生成されたコードを見てみましょう。 次の 3 つのクラスがあります。

- **mnistModel** は、機械学習モデルの表現を作成し、システムの既定のデバイスでセッションを作成し、特定の入力と出力をモデルにバインドして、モデルを非同期に評価します。
- **mnistInput** は、モデルが想定する入力の型を初期化します。 この場合、入力には [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue) が想定されます。
- **mnistOutput** は、モデルによる出力の型を初期化します。 この場合、出力は、[TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat) 型の **Plus214_Output_0** というリストになります。

これらのクラスを使って、プロジェクトでモデルを読み込み、バインドし、評価していきます。

## <a name="5-load-bind-and-evaluate-the-model"></a>5.モデルの読み込み、バインド、評価を行う

Windows ML アプリケーションでは、次のパターンに従う必要があります。読み込み > バインド > 評価。

1. 機械学習モデルを読み込む。
2. 入力と出力をモデルにバインドする。
3. モデルを評価して結果を確認する。

ここでは、**mnist.cs** に生成されたインターフェイス コードを使って、アプリケーションでモデルを読み込み、バインドし、評価します。

最初に、**MainPage.xaml.cs** で、モデル、入力、出力をインスタンス化します。 次のメンバー変数を **MainPage** クラスに追加します。

```csharp
private mnistModel ModelGen;
private mnistInput ModelInput = new mnistInput();
private mnistOutput ModelOutput;
```

その後、**LoadModelAsync** でモデルを読み込みます。 このメソッドは、モデルのいずれかのメソッドを使用する前に (つまり、**MainPage** の [Loaded](https://docs.microsoft.com/uwp/api/windows.ui.xaml.frameworkelement.loaded) イベントで、[OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto) オーバーライドで、または **recognizeButton_Click** が呼び出される前の任意の場所で) 呼び出す必要があります。 **mnistModel** クラスは、MNIST モデルを表し、システムの既定のデバイスでセッションを作成します。 モデルを読み込むには、**CreateFromStreamAsync** メソッドを呼び出し、パラメーターとして ONNX ファイルを渡します。

```csharp
private async Task LoadModelAsync()
{
    // Load a machine learning model
    StorageFile modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Assets/mnist.onnx"));
    ModelGen = await mnistModel.CreateFromStreamAsync(modelFile as IRandomAccessStreamReference);
}
```

> [!NOTE]
> **IRandomAccessStreamReference** の下に赤い下線が表示された場合は、その名前空間を含める必要があります。 その上にカーソルを置き、**Ctrl + .** キーを押して、 ドロップダウン メニューから **[using Windows.Storage.Streams]** を選択します。

次に、入力と出力をモデルにバインドします。 生成されたコードには、**mnistInput** と **mnistOutput** のラッパー クラスも含まれています。 **mnistInput** クラスはモデルが想定する入力を表し、**mnistOutput** クラスはモデルが想定する出力を表します。

モデルの入力オブジェクトを初期化するには、**mnistInput** クラスのコンストラクターを呼び出して、アプリケーション データを渡します。このとき、入力データが、モデルが想定する入力型と一致している必要があります。 **mnistInput** クラスは **ImageFeatureValue** を想定しているため、ここではヘルパー メソッドを使って入力用の **ImageFeatureValue** を取得します。

**helper.cs** に含まれるヘルパー関数を使って、**InkCanvas** の内容をコピーし、**ImageFeatureValue** 型に変換して、モデルにバインドします。

```csharp
private async void recognizeButton_Click(object sender, RoutedEventArgs e)
{
    // Bind model input with contents from InkCanvas
    VideoFrame vf = await helper.GetHandWrittenImage(inkGrid);
    ModelInput.Input3 = ImageFeatureValue.CreateFromVideoFrame(vf);
}
```

出力は、指定された入力で **EvaluateAsync** を呼び出すだけです。 入力が初期化されたら、モデルの **EvaluateAsync** メソッドを呼び出して、入力データに対してモデルを評価します。 **EvaluateAsync** は、入力と出力をモデル オブジェクトにバインドし、入力に対してモデルを評価します。

モデルからは出力テンソルが返されるため、まずそれをわかりやすいデータ型に変換してから、返されたリストを解析して、最も可能性の高い数字を判断し、それを表示する必要があります。

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

最後に、**InkCanvas** を消去して、ユーザーが別の数字を描画できるようにします。

```csharp
private void clearButton_Click(object sender, RoutedEventArgs e)
{
    inkCanvas.InkPresenter.StrokeContainer.Clear();
    numberLabel.Text = "";
}
```

## <a name="6-launch-the-application"></a>6.アプリケーションを起動する

アプリケーションをビルドして起動する (**F5** キーを押す) と、**InkCanvas** に描画された数字を認識できるようになります。

![完成したアプリケーション](../images/get-started4.png)

これで初めての Windows ML アプリケーションが完成しました。 Windows ML の使い方を紹介する他のサンプルについては、GitHub の [Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning) をリポジトリを確認してください。

[!INCLUDE [help](../includes/get-help.md)]
