---
author: eliotcowley
title: モデルをバインドします。
description: モデルの入力と出力に、およびモデルから情報を渡すためにバインドする方法について説明します。
ms.author: elcowle
ms.date: 2/15/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: 52c63768834f384884463035a8fba0efe031b85f
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474319"
---
# <a name="bind-a-model"></a>モデルをバインドします。

機械学習モデルに入力と出力の機能は、モデルとの間の情報を渡します。

として、モデルの読み込み後、 [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)、使用することができます[LearningModel.InputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.inputfeatures)と[LearningModel.OutputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.outputfeatures)させる[ILearningModelFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor)オブジェクト。 これらの一覧、モデルの入力と機能の種類の出力します。

使用する、 [LearningModelBinding](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding) 、機能に値をバインドするを参照する、 **ILearningModelFeatureDescriptor**によってその[名前](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor.name)プロパティ。

次のビデオでは、バインディングの機械学習モデルの機能の概要を示します。

<br/>

> [!VIDEO https://www.youtube.com/embed/WD5bNZwz2A8]

## <a name="types-of-features"></a>機能の種類

Windows の ML 内に列挙されたすべての ONNX 機能型をサポートしている[LearningModelFeatureKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelfeaturekind)します。 これらは、さまざまな機能の記述子のクラスにマップされます。

* **利用したテンソル**:[TensorFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfeaturedescriptor)
* **シーケンス**:[SequenceFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.sequencefeaturedescriptor)
* **マップ**:[MapFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.mapfeaturedescriptor)
* **イメージ**:[ImageFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturedescriptor)

### <a name="tensors"></a>Tensors

Tensors は多次元配列、および最も一般的な tensor は 32 ビットの浮動小数点値を利用したテンソルします。 Tensors のディメンションでは、行優先が緊密にパックされた連続するデータが各ディメンションを表します。 利用したテンソルの合計サイズは、各次元のサイズの積です。

### <a name="sequences"></a>シーケンス

シーケンスは、値のベクトルです。 シーケンス型の一般的な用途は、各予測の精度の評価を示すいくつかの分類モデルを返す float 確率のベクトルです。 

### <a name="maps"></a>マップ

マップは、情報のキー/値ペアです。 分類モデルはよく、各分類のラベルが付いた名前の float 確率を説明する文字列/float マップを返します。 たとえば、画像の犬の種類を予測しようとするモデルの出力があります`["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`します。

#### <a name="scalars"></a>スカラー

ほとんどのマップおよびシーケンスは、スカラー値を持ちます。 これらの場所を表示**TensorFeatureDescriptor.Shape.Size**はゼロ (0)。 ここでは、マップまたはシーケンスは、スカラー型になります。 最も一般的な`float`します。 たとえば、マップを float への文字列は次のようになります。

```cs
MapFeatureDescriptor.KeyKind == TensorKind.String
MapFeatureDescriptor.ValueDescriptor.Kind == LearningModelFeatureKind.Tensor
MapFeatureDescriptor.ValueDescriptor.as<TensorFeatureDescriptor>().Shape.Size == 0
```

実際のマップ機能の値になります、`IMap<string, float>`します。

### <a name="images"></a>画像

イメージを使用する場合は、イメージ形式と tensorization を意識する必要があります。

#### <a name="image-formats"></a>イメージの形式

イメージのトレーニング データでモデルがトレーニングし、重みが保存され、そのトレーニング セットに合わせて調整します。 イメージをモデルに入力を渡すときに、その形式は、トレーニングのイメージ形式と一致する必要があります。

多くの場合、モデルが、必要なイメージ形式を説明します。ONNX モデルを使用できる[メタデータ](https://github.com/onnx/onnx/blob/master/docs/MetadataProps.md)に必要なイメージ形式について説明します。  

ほとんどのモデルは、次の形式を使用して、すべてのモデルにユニバーサルではありません。

* **Image.BitmapPixelFormat**:Bgr8
* **Image.ColorSpaceGamma**:SRGB
* **Image.NominalPixelRange**:NominalRange_0_255

#### <a name="tensorization"></a>Tensorization

イメージは、Windows の ML で利用したテンソル形式で表現されます。 Tensorization を利用したテンソルにイメージを変換するプロセスは、バインド中に発生します。

Windows の ML では、4 次元 tensors「NCHW tensor 形式」で 32 ビットの浮動小数点値にイメージを変換します。

* **N**:バッチ サイズ (またはイメージの数)。 Windows の ML には、1 のバッチ サイズ N 現在サポートしています。
* **C**:チャネルの数 (Gray8、Bgr8 3 の 1)。
* **H**:高さ。
* **W**:幅。

各ピクセルのイメージは、0 ~ 255 の範囲に格納され、32 ビット浮動小数点数にパックする 8 ビット色数です。

#### <a name="how-to-pass-images-into-the-model"></a>イメージをモデルに渡す方法

イメージは、モデルに渡すことができます 2 つの方法はあります。

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)

    使用することをお勧めします。 **ImageFeatureValue**変換と tensorization の両方の処理には、入力と出力としてイメージをバインドするにように、イメージと一致、モデルの必要なイメージ形式。 現在サポートされているモデル形式の種類は**Gray8**、 **Rgb8**、および**Bgr8**、現在サポートされているピクセルの範囲は 0 ~ 255 とします。

    作成することができます、 **ImageFeatureValue**静的メソッドを使用して[ImageFeatureValue.CreateFromVideoFrame](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue.createfromvideoframe)します。

    モデルの形式を確認する必要があります、WinML は、次のロジックと優先順位の順序を使用します。

    1. [バインド (String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_)イメージのすべての設定が上書きされます。
    2. モデル メタデータをチェックし、および使用可能な場合に使用されます。
    3. モデルのメタデータが指定されていない呼び出し元にプロパティが指定されていない場合は、ランタイムは最適な一致を作成しようとします。 NCHW ようテンソル場合 (4 次元 float32、N 1 = =)、ランタイムはいずれかを想定していますが**Gray8**または**Bgr8**チャネルの数によって異なります。

    いくつかの省略可能なプロパティに渡すことができる[バインド (String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_):

    * [BitmapBounds](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapbounds):指定すると場合、これらは、トリミング境界をモデルにイメージを送信する前に適用します。
    * [BitmapPixelFormat](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmappixelformat):指定した場合は、イメージの変換中にモデルのピクセル形式として使用されるピクセル形式になります。

    イメージ図形は、モデルは、いずれかの特定の図形 (たとえば、SqueezeNet は 224,224) かかること、または、モデルは、任意図形のイメージ (StyleTransfer 型の多くのモデルは、可変サイズの画像をかかることができます) の無料の寸法を指定できますを指定できます。 呼び出し元が使用できる**BitmapBounds**のどのセクションで、イメージ扱おうとする使用を選択します。 指定しない場合、ランタイムが (縦横比を考慮し) モデルのサイズにスケーリングし、トリミングをし、中央します。  

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)

    Windows の ML にモデルの色形式またはピクセルの範囲ができない場合は、変換と tensorization を実装できます。 入力の値は、32 ビット浮動小数点数の NCHW 4 次元 tensor を作成します。 参照してください、[カスタム Tensorization サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)これを行う方法の例についてはします。

    このメソッドを使用すると、モデルのすべてのイメージ メタデータが無視されます。

## <a name="example"></a>例

次の例では、モデルの入力にバインドする方法を示します。 バインドを作成するこの例では、*セッション*、作成、 **ImageFeatureValue**から*inputFrame*、およびモデルにイメージの入力、bind *inputName*.

```cs
private void BindModel(
    LearningModelSession session, 
    VideoFrame inputFrame, 
    string inputName) 
{
    // Create a binding object from the session
    LearningModelBinding binding = new LearningModelBinding(session);

    // Create an image tensor from a video frame
    ImageFeatureValue image = 
        ImageFeatureValue.CreateFromVideoFrame(inputFrame);

    // Bind the image to the input
    binding.Bind(inputName, image);
}
```

## <a name="see-also"></a>関連項目

* 先の：[セッションを作成します。](create-a-session.md)
* 次に：[モデルの入力を評価します。](evaluate-model-inputs.md)

[!INCLUDE [help](includes/get-help.md)]
