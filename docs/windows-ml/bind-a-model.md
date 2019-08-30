---
title: モデルを作成する
description: モデルの入力と出力をバインドして、モデルとの間で情報を渡す方法について説明します。
ms.date: 5/29/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: abffa39c066abb49bf74d528722a29432c2543b2
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156183"
---
# <a name="bind-a-model"></a>モデルを作成する

機械学習モデルには、入力と出力の機能があります。この機能は、モデルとの間で情報をやり取りします。

[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)としてモデルを読み込んだ後、 [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.inputfeatures)と[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.outputfeatures)を使用して[ILearningModelFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor)オブジェクトを取得できます。 これらの一覧には、モデルの期待される入力と出力の機能の種類が表示されます。

[LearningModelBinding](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding)を使用して、 **ILearningModelFeatureDescriptor**を[Name](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.ilearningmodelfeaturedescriptor.name)プロパティで参照する機能に値をバインドします。

次のビデオでは、機械学習モデルのバインド機能の概要を簡単に説明します。

<br/>

> [!VIDEO https://www.youtube.com/embed/WD5bNZwz2A8]

## <a name="types-of-features"></a>機能の種類

Windows ML は、 [LearningModelFeatureKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelfeaturekind)で列挙されるすべての ONNX 機能の種類をサポートしています。 これらは、さまざまな特徴記述子クラスにマップされます。

* 次のようになります。[TensorFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfeaturedescriptor)
* **シーケンス**:[SequenceFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.sequencefeaturedescriptor)
* **マップ**:[MapFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.mapfeaturedescriptor)
* **イメージ**:[ImageFeatureDescriptor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturedescriptor)

### <a name="tensors"></a>Tensors

Tensors は多次元配列であり、最も一般的なのは、32ビットの浮動小数点数です。 Tensors のディメンションは行メジャーであり、各ディメンションを表す連続したデータが厳密にパックされています。 この合計サイズは、各ディメンションのサイズの積です。

### <a name="sequences"></a>シーケンス

シーケンスは、値のベクターです。 シーケンス型の一般的な使用方法は、float 確率のベクターです。これは、各予測の精度の評価を示すために返される分類モデルです。

### <a name="maps"></a>マップ

マップは、情報のキーと値のペアです。 通常、分類モデルは、ラベル付けされた各分類名の float 確率を表す文字列/浮動小数点マップを返します。 たとえば、画像の犬の組み合わせを予測しようとするモデルの出力は、のよう`["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`になります。

#### <a name="scalars"></a>スカラー

ほとんどのマップとシーケンスは、スカラー値を持ちます。 これらは、保存場所がゼロ (0) であることを示しています。 この場合、マップまたはシーケンスはスカラー型になります。 最も一般的なの`float`はです。 たとえば、マップする文字列は次のようになります。

```cs
MapFeatureDescriptor.KeyKind == TensorKind.String
MapFeatureDescriptor.ValueDescriptor.Kind == LearningModelFeatureKind.Tensor
MapFeatureDescriptor.ValueDescriptor.as<TensorFeatureDescriptor>().Shape.Size == 0
```

実際のマップ機能の値はに`IMap<string, float>`なります。

#### <a name="sequence-of-maps"></a>マップのシーケンス

一連のマップは、キーと値のペアのベクターにすぎません。 たとえば、文字列から浮動小数点数へのマップのシーケンスは型`IVector<IMap<string, float>>`になります。 犬の予測`["Boston terrier", 90.0], ["Golden retriever", 7.4], ["Poodle", 2.6]`の上記の出力は、一連のマップの一例です。

### <a name="images"></a>画像

イメージを操作する場合は、イメージ形式に注意する必要があります。

#### <a name="image-formats"></a>画像の形式

モデルは、イメージトレーニングデータでトレーニングされます。重みは、そのトレーニングセットに合わせて保存され、調整されます。 イメージ入力をモデルに渡すときは、その形式がトレーニングイメージの形式と一致している必要があります。

多くの場合、モデルは予想されるイメージ形式を表します。ONNX モデルでは、[メタデータ](https://github.com/onnx/onnx/blob/master/docs/MetadataProps.md)を使用して、予想されるイメージ形式を記述できます。  

ほとんどのモデルでは次の形式が使用されますが、これはすべてのモデルに対して汎用的ではありません。

* **BitmapPixelFormat**:Bgr8
* **イメージ。 Colorspace ガンマ**:SRGB
* **NominalPixelRange**:NominalRange_0_255

#### <a name="tensorization"></a>すべてのものを

イメージは、Windows ML では、その形式で表示されます。 これは、イメージをオートに変換するプロセスであり、バインド中に発生します。

Windows ML では、"NCHW tensors" という形式で、イメージが32ビットの浮動小数点数に変換されます。

* **N**:バッチサイズ (またはイメージの数)。 Windows ML では、現在、バッチサイズ N の1がサポートされています。
* **C**:チャネル数 (Gray8 の場合は1、Bgr8 の場合は 3)。
* **H**:上下.
* **W**:幅。

イメージの各ピクセルは、0-255 の範囲に格納され、32ビットの浮動小数点数にパックされる8ビットのカラー番号です。

#### <a name="how-to-pass-images-into-the-model"></a>モデルにイメージを渡す方法

イメージをモデルに渡すには、次の2つの方法があります。

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)

    **Imagefeaturevalue**を使用して、画像を入力および出力としてバインドすることをお勧めします。これは、変換と変換の両方が処理されるため、イメージはモデルの必要なイメージ形式と一致するためです。 現在サポートされているモデル形式の種類は**Gray8**、 **Rgb8**、および**Bgr8**で、現在サポートされているピクセル範囲は0-255 です。

    Imagefeaturevalue を作成するには、静的なメソッド[Imagefeaturevalue. CreateFromVideoFrame](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue.createfromvideoframe)を使用します。

    モデルで必要な形式を確認するために、WinML は次のロジックと優先順位を使用します。

    1. [Bind (String, Object, IPropertySet) は、](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_)すべてのイメージ設定を上書きします。
    2. モデルのメタデータはチェックされ、使用可能な場合は使用されます。
    3. モデルメタデータが指定されておらず、呼び出し元が指定したプロパティがない場合、ランタイムは最適な照合を試みます。 このようにしても、NCHW (4 次元の float32, N = = 1) のように見える場合、ランタイムはチャネル数に応じて**Gray8**または**Bgr8**のいずれかを想定します。

    Bind に渡すことができる省略可能なプロパティがいくつかあります[(String、Object、IPropertySet)](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind#Windows_AI_MachineLearning_LearningModelBinding_Bind_System_String_System_Object_Windows_Foundation_Collections_IPropertySet_)。

    * [Bitmapbounds](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapbounds):指定されている場合、これらは、モデルにイメージを送信する前に適用するトリミング境界です。
    * [BitmapPixelFormat](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmappixelformat):指定した場合、イメージの変換中にモデルのピクセル形式として使用されるピクセル形式になります。

    イメージ図形の場合、モデルでは、実行する特定の図形 (たとえば、SqueezeNet が224224を受け取る) を指定することも、モデルで任意の図形イメージの自由ディメンションを指定することもできます (多くのスタイル転送タイプのモデルは可変サイズのイメージを使用できます)。 呼び出し元は、 **Bitmapbounds**を使用して、使用するイメージのセクションを選択できます。 指定しない場合、ランタイムはイメージをモデルサイズ (縦横比を考慮) にスケーリングし、次にセンタートリミングします。  

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)

    Windows ML でモデルのカラーフォーマットまたはピクセル範囲がサポートされていない場合は、変換を実装して、変換を行うことができます。 入力値として、32ビット浮動小数点値の NCHW を作成します。 これを行う方法の例については、「カスタムの管理」の[サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)を参照してください。

    このメソッドを使用すると、モデルのイメージメタデータはすべて無視されます。

## <a name="example"></a>例

次の例は、モデルの入力にバインドする方法を示しています。 この場合は、*セッション*からバインドを作成し、 *Inputframe*から**imagefeaturevalue**を作成し、そのイメージをモデルの入力*inputframe*にバインドします。

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

* 先の：[セッションを作成する](create-a-session.md)
* 次の手順:[モデルの入力を評価する](evaluate-model-inputs.md)

[!INCLUDE [help](../includes/get-help.md)]
