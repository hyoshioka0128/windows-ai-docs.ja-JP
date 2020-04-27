---
title: モデルを作成する
description: モデルとの間で情報をやり取りするためにモデルの入力と出力をバインドする方法について説明します。
ms.date: 5/29/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: a2f83c0b3eedc64019e6c60fbc3d14cdb573a524
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "75216965"
---
# <a name="bind-a-model"></a>モデルを作成する

機械学習モデルには、モデルとの間で情報をやり取りする入力および出力機能があります。

モデルを [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) として読み込んだ後、[LearningModel.InputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.inputfeatures) と [LearningModel.OutputFeatures](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.outputfeatures) を使用して [ILearningModelFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor) オブジェクトを取得できます。 これらにより、モデルで想定される入力および出力機能の型が一覧表示されます。

値を機能にバインドし、その [Name](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor.name) プロパティで **ILearningModelFeatureDescriptor** を参照するには、[LearningModelBinding](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding) を使用します。

次のビデオは、機械学習モデルのバインド機能の概要を簡単に紹介したものです。

<br/>

> [!VIDEO https://www.youtube.com/embed/WD5bNZwz2A8]

## <a name="types-of-features"></a>機能の型

Windows ML は、[LearningModelFeatureKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelfeaturekind) で列挙されるすべての ONNX 機能の型をサポートしています。 これらは、次のさまざまな機能記述子クラスにマップされます。

* **テンソル**: [TensorFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfeaturedescriptor)
* **シーケンス**: [SequenceFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.sequencefeaturedescriptor)
* **マップ**: [MapFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.mapfeaturedescriptor)
* **イメージ**: [ImageFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturedescriptor)

### <a name="tensors"></a>テンソル

テンソルは多次元配列であり、最も一般的なテンソルは 32 ビット浮動小数点数のテンソルです。 テンソルのディメンションは行優先であり、各ディメンションを表す緊密にパックされた連続データを含みます。 テンソルの合計サイズは、各ディメンションのサイズの積です。

### <a name="sequences"></a>シーケンス

シーケンスは、値のベクトルです。 シーケンス型の一般的な使用法は、浮動小数点数の確率のベクトルです。これは、一部の分類モデルから返され、予測ごとの精度の評価を示します。

### <a name="maps"></a>マップ

マップは、情報のキーと値のペアです。 分類モデルは一般に、ラベルの付いた分類名ごとの浮動小数点数の確率が記述された文字列/浮動小数点数のマップを返します。 たとえば、画像内の犬の種類を予測しようとするモデルの出力が `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]` になることがあります。

#### <a name="scalars"></a>スカラー

ほとんどのマップやシーケンスにはスカラー値があります。 これらは、**TensorFeatureDescriptor.Shape.Size** が 0 である場合に表示されます。 この場合、マップまたはシーケンスはスカラー型になります。 最も一般的なのは `float` です。 たとえば、文字列から浮動小数点数へのマップは次のようになります。

```cs
MapFeatureDescriptor.KeyKind == TensorKind.String
MapFeatureDescriptor.ValueDescriptor.Kind == LearningModelFeatureKind.Tensor
MapFeatureDescriptor.ValueDescriptor.as<TensorFeatureDescriptor>().Shape.Size == 0
```

実際のマップ機能の値は `IMap<string, float>` になります。

#### <a name="sequence-of-maps"></a>マップのシーケンス

マップのシーケンスは、単なるキーと値のペアのベクトルです。 たとえば、文字列から浮動小数点数へのマップのシーケンスは型 `IVector<IMap<string, float>>` になります。 犬の種類の予測に関する上の出力 `["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]` は、マップのシーケンスの例です。

### <a name="images"></a>イメージ

イメージを操作する場合は、イメージ形式とテンソル化に注意する必要があります。

#### <a name="image-formats"></a>イメージ形式

モデルがイメージ トレーニング データでトレーニングされた後、重みが保存され、そのトレーニング セットに対して調整されます。 イメージ入力をモデルに渡す場合は、その形式がトレーニング イメージの形式に一致している必要があります。

多くの場合、モデルは想定されるイメージ形式を記述します。ONNX モデルは、[メタデータ](https://github.com/onnx/onnx/blob/master/docs/MetadataProps.md)を使用して想定されるイメージ形式を記述できます。  

ほとんどのモデルは次の形式を使用しますが、これはすべてのモデルに対して汎用性があるわけではありません。

* **Image.BitmapPixelFormat**: Bgr8
* **Image.ColorSpaceGamma**: SRGB
* **Image.NominalPixelRange**: NominalRange_0_255

#### <a name="tensorization"></a>テンソル化

Windows ML では、イメージはテンソル形式で表されます。 テンソル化は、イメージをテンソルに変換するプロセスであり、バインド中に発生します。

Windows ML は、イメージを "NCHW テンソル形式" の 32 ビット浮動小数点数の 4 次元テンソルに変換します。

* **N**: バッチ サイズ (またはイメージの数)。 Windows ML は現在、1 のバッチ サイズ N をサポートしています。
* **C**: チャネル数 (Gray8 では 1、Bgr8 では 3)。
* **H**: 高さ。
* **W**: 幅。

イメージの各ピクセルは、0-255 の範囲に格納され、32 ビット浮動小数点数にパックされる 8 ビットの色番号です。

#### <a name="how-to-pass-images-into-the-model"></a>イメージをモデルに渡す方法

イメージは、次の 2 つの方法でモデルに渡すことができます。

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)

    イメージを入力と出力としてバインドするには、**ImageFeatureValue** を使用することをお勧めします。これは変換とテンソル化の両方を処理するため、イメージがモデルの必要なイメージ形式に一致します。 現在サポートされているモデル形式の種類は **Gray8**、**Rgb8**、および **Bgr8** であり、サポートされているピクセル範囲は 0-255 です。

    **ImageFeatureValue** は、静的メソッド [ImageFeatureValue.CreateFromVideoFrame](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue.createfromvideoframe) を使用して作成できます。

    モデルにどのような形式が必要かを見つけるために、WinML は次のロジックと優先順位を使用します。

    1. [Bind(String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_) で、すべてのイメージ設定がオーバーライドされます。
    2. その後、モデル メタデータがチェックされ、可能であれば使用されます。
    3. モデル メタデータが指定されておらず、どの呼び出し元もプロパティを指定しなかった場合は、ランタイムが最適な一致を試みます。 
    * テンソルが NCHW (4 次元 float32、N==1) である可能性がある場合、ランタイムは、チャネル数に応じて **Gray8** (C==1) または **Bgr8** (C==3) のどちらかを想定します。
    * NominalRange_0_255 が想定されます。
    * SRGB が想定されます。

    [Bind(String, Object, IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_) には、次のいくつかのオプション プロパティを渡すことができます。

    * [BitmapBounds](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapbounds): 指定されている場合、これらは、イメージをモデルに送信する前に適用するトリミング境界です。
    * [BitmapPixelFormat](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmappixelformat): 指定されている場合、これは、イメージの変換中にモデルのピクセル形式として使用されるピクセル形式です。

    イメージ シェイプの場合、モデルは受け取る特定のシェイプを指定できます (たとえば、SqueezeNet は 224,224 を受け取ります)。または、シェイプ イメージの場合、モデルはフリー ディメンションを指定できます (多くの StyleTransfer タイプのモデルは可変サイズのイメージを受け取ることができます)。 呼び出し元は、**BitmapBounds** を使用して、イメージのどのセクションを使用するかを選択できます。 指定されていない場合、ランタイムは (縦横比を考慮して) イメージをモデル サイズにスケーリングしてから、センター トリミングします。  

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)

    Windows ML でモデルの色形式またはピクセル範囲がサポートされていない場合は、変換とテンソル化を実装できます。 入力値に対して 32 ビット浮動小数点数の NCHW 4 次元テンソルを作成します。 この実行方法の例については、[カスタム テンソル化のサンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)に関するページを参照してください。

    この方法が使用された場合、モデル上のイメージ メタデータはすべて無視されます。

## <a name="example"></a>例

次の例は、モデルの入力にバインドする方法を示しています。 この場合は、*session* からバインドを作成し、*inputFrame* から **ImageFeatureValue** を作成した後、イメージをモデルの入力 *inputName* にバインドします。

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

* 前の手順: [セッションを作成する](create-a-session.md)
* 次の手順:[モデルの入力を評価する](evaluate-model-inputs.md)

[!INCLUDE [help](../includes/get-help.md)]
