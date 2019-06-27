---
author: walrusmcd
title: Windows の ML パフォーマンスとメモリ
description: Windows の ML を使用する場合、アプリケーションのパフォーマンスを向上させる方法について説明します。
ms.author: paulm
ms.date: 6/24/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 7b858e143af00ed0bf3c34986b07a0ad1f3dc01d
ms.sourcegitcommit: edfaeda957977f26056b425a5cdda73d7a4f4ea1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2019
ms.locfileid: "67334131"
---
# <a name="windows-ml-performance-and-memory"></a>Windows の ML パフォーマンスとメモリ

この記事では、Windows Machine Learning を使用する場合は、アプリケーションのパフォーマンスを向上させる方法を取り上げます。

## <a name="memory-utilization"></a>メモリ使用率

各インスタンス[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)と[LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession)メモリ内モデルのコピーが存在します。 考慮、可能性がありますされません小さなモデルを使用している場合は、非常に大きなモデルを使用している場合は、これが重要になります。

メモリを解放するには、呼び出す**Dispose**モデルまたはセッションのいずれかにします。 一部の言語は、レイジー ガベージ コレクションを実行して、値を削除しないでくださいだけです。

**LearningModel**新しいセッションの作成を有効にするメモリ内コピーを保持します。 破棄するときに、 **LearningModel**、既存のすべてのセッションは引き続き機能します。  ただしは不要になったことできますと新しいセッションを作成する**LearningModel**インスタンス。 大規模なモデルは、モデルとセッションを作成し、モデルを破棄できます。 すべての呼び出しに 1 つのセッションを使用して、 [Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate)メモリ内で大規模なモデルの 1 つのコピーを必要があります。

<!--
<TODO Asynchronous calling patterns>
-->

## <a name="float16-support"></a>Float16 サポート

パフォーマンスを向上させると縮小のモデルのフット プリントは、使用することができます[WinMLTools](convert-model-winmltools.md#convert-to-floating-point-16) float16 モデルに変換します。

変換されると、すべての重みと入力 float16 がされます。 Float16 入力と出力を操作する方法を次に示します。

* [ImageFeatureValue](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)
    * 推奨される使用法。
    * 色を変換し、tensorizes float16 にします。
    * 8 ビットのイメージ形式は、データ損失のない float16 に安全に変換できる bgr8 をサポートします。

* [TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)
    * 高度なパスです。
    * Float32 float16 にキャストします。
    * イメージでは、これは、安全にキャスト、bgr8 が小さいと適合します。
    * イメージ以外の場合、[バインド](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelbinding.bind)は失敗とする必要がありますを渡す、 [TensorFloat16Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit)代わりにします。

* [TensorFloat16Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit)
    * 高度なパスです。
    * Float16 に変換し、float32 float16 にキャストとして入力を渡す必要があります。

> [!NOTE]
> ほとんどの場合、演算子では 32 ビットの数値演算は実行もします。 、オーバーフローのリスクを低減し、結果が float16 に切り捨てられます。 ただし、float16 サポートをアドバタイズするハードウェア、ランタイムはこれの利点を実行します。

## <a name="pre-processing-input-data"></a>処理前の入力データ

WinML は、内部入力のデータより簡単かつ効率的に処理することでいくつかの処理前の手順を実行します。 たとえば、入力画像の指定された色形式と、図形のさまざまな可能性があります。 し、モデルが必要ですが異なる可能性があります。 WinML は、開発者の負荷を減らすとに一致させるイメージに変換を実行します。

WinML では、シナリオと、特定のデバイス (CPU、GPU、およびなど)、最も効率的な変換を提供する、ハードウェア全体スタックも利用します。

ただし、場合によってはいくつかの要件があるため、入力データを手動で tensorize たい場合があります。 たとえば、おそらくたくを使用する[VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe)画像、または 0 ~ 1 の範囲を 0 ~ 255 の範囲からのピクセル値を正規化するためです。 このような場合は、データを独自のカスタム tensorization を行うことができます。 参照してください、[カスタム Tensorization サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)これの例についてはします。

[!INCLUDE [help](../includes/get-help.md)]
