---
author: walrusmcd
title: Windows ML のパフォーマンスとメモリ
description: Windows ML の使用時にアプリケーションのパフォーマンスを向上させる方法について説明します。
ms.author: paulm
ms.date: 6/24/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 7b858e143af00ed0bf3c34986b07a0ad1f3dc01d
ms.sourcegitcommit: edfaeda957977f26056b425a5cdda73d7a4f4ea1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2019
ms.locfileid: "67334131"
---
# <a name="windows-ml-performance-and-memory"></a>Windows ML のパフォーマンスとメモリ

この記事では、Windows Machine Learning の使用時にアプリケーションのパフォーマンスを向上させる方法について説明します。

## <a name="memory-utilization"></a>メモリ使用率

[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) と [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession) の各インスタンスには、メモリ内にモデルのコピーがあります。 小規模なモデルを操作している場合は心配ないかもしれませんが、非常に大規模なモデルを操作している場合はこれが重要になります。

メモリを解放するには、モデルまたはセッションで **Dispose** を呼び出します。 それらを単純に削除しないでください。一部の言語ではレイジー ガベージ コレクションが実行されるためです。

**LearningModel** は、新しいセッションを作成できるように、メモリ内にコピーを保持します。 **LearningModel** を破棄した場合、既存のすべてのセッションは引き続き機能します。  ただし、その **LearningModel** インスタンスを使用して新しいセッションを作成できなくなります。 大規模なモデルでは、モデルとセッションを作成し、後でそのモデルを破棄できます。 [Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate) のすべての呼び出しに対して 1 つのセッションを使用すると、メモリ内に大規模なモデルのコピーを 1 つ保持することになります。

<!--
<TODO Asynchronous calling patterns>
-->

## <a name="float16-support"></a>Float16 のサポート

パフォーマンスの向上と、モデルのフットプリントの削減のために、[WinMLTools](convert-model-winmltools.md#convert-to-floating-point-16) を使用して、モデルを float16 に変換できます。

変換されると、すべての重みと入力が float16 になります。 float16 の入力と出力を操作する方法を次に示します。

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)
    * 推奨される使用法です。
    * 色を float16 に変換し、テンソル化します。
    * bgr8 および 8 ビットの画像形式をサポートしており、データ損失なしで float16 に安全に変換できます。

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)
    * 高度な方法。
    * float32 を float16 に型変換します。
    * 画像の場合、bgr8 はサイズが小さくて収まるので、これは安全に型変換できます。
    * 画像以外の場合、[Bind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind) は失敗し、代わりに [TensorFloat16Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit) に渡す必要があります。

* [TensorFloat16Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit)
    * 高度な方法。
    * float16 に変換し、入力を float32 として渡す必要があります。これが float16 に型変換されます。

> [!NOTE]
> ほとんどの場合、オペレーターは 32 ビット演算を依然として実行しています。 オーバーフローのリスクは少なく、結果は float16 に切り捨てられます。 ただし、ハードウェアで float16 のサポートが公表されている場合、それがランタイムで利用されます。

## <a name="pre-processing-input-data"></a>入力データの前処理

WinML では、入力データの処理をより簡単かつ効率的に行うために、内部でいくつかの前処理手順が実行されます。 たとえば、指定された入力画像はさまざまな色の形式や形状である可能性があり、モデルで想定されるものとは異なることがあります。 WinML では画像に対して変換を実行して一致させるため、開発者の負担が軽減されます。

また、WinML は、(CPU、GPU などの) ハードウェア スタック全体を利用して、特定のデバイスとシナリオに最も効率的な変換を提供します。

ただし、場合によっては、特定の要件があるために、入力データを手動でテンソル化しなければならないことがあります。 たとえば、画像に [VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe) を使用したくない場合や、ピクセル値を 0 から 255 の範囲から、0 から 1 の範囲に正規化する場合などです。 このような場合は、データに対して独自のカスタム テンソル化を実行できます。 この例については、[カスタム テンソル化のサンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)を参照してください。

[!INCLUDE [help](../includes/get-help.md)]
