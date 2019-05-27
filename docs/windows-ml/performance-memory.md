---
author: walrusmcd
title: Windows の ML パフォーマンスとメモリ
description: Windows の ML を使用する場合、アプリのパフォーマンスを向上させる方法について説明します。
ms.author: paulm
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: b51e01e20433aa8314a99baadc06cc9b0767f665
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180064"
---
# <a name="windows-ml-performance-and-memory"></a>Windows の ML パフォーマンスとメモリ

この記事では、Windows の ML を使用する場合、アプリのパフォーマンスを向上させる方法を取り上げます。

## <a name="memory-utilization"></a>メモリ使用率

各インスタンス[ **LearningModel** ](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)と[ **LearningModelSession** ](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession)メモリ内モデルのコピーが存在します。 考慮、可能性がありますされません小さなモデルを使用している場合は、非常に大きなモデルを使用している場合は、これが重要になります。

メモリを解放するには、モデルまたはセッションのいずれかで Dispose() を呼び出します。 一部の言語は、レイジー ガベージ コレクションを実行して、値を削除しないでくださいだけです。

**LearningModel**新しいセッションの作成を有効にするメモリ内コピーを保持します。 LearningModel を破棄するときに、既存のすべてのセッションは機能し続けます。  ただし、するできなく LearningModel インスタンスを新しいセッションを作成できません。 大規模なモデルは、モデルとセッションを作成し、モデルを破棄できます。 Evaluate() にすべての呼び出しに対して 1 つのセッションを使用して、メモリ内で大規模なモデルの 1 つのコピーが必要があります。

<TODO Asynchronous calling patterns>

## <a name="float16-support"></a>Float16 サポート

パフォーマンスを向上させると縮小のモデルのフット プリントは、使用することができます[WinMLTools](convert-model-winmltools.md#convert-to-floating-point-16) float16 モデルに変換します。

変換されると、すべての重みと入力 float16 がされます。 Float16 入力と出力を操作する方法を次に示します。

* [**ImageFeatureValue**](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.imagefeaturevalue)
    * 推奨される使用法。
    * 色を変換し、tensorizes float16 にします。
    * データ損失なし float16 に安全に変換できる bgr8 と 8 ビットのイメージ形式をサポートしています。  
* [**TensorFloat**](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)
    * 高度なパスです。
    * Float32 float16 にキャストします。
    * イメージでは、この安全キャスト、bgr8 が小さく、収まるようにします。
    * イメージ以外の場合、Bind() は失敗すると、および、TensorFloat16Bit 代わりに渡す必要があります。
* [**TensorFloat16Bit**](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat16bit)
    * 高度なパスです。
    * Float16 に変換し、float32 float16 にキャストとして入力を渡す必要があります。

**注意**:ほとんどの場合、演算子では 32 ビットの数値演算は実行もします。 、オーバーフローのリスクを低減し、結果が float16 に切り捨てられます。 ただし、float16 サポートをアドバタイズするハードウェア、ランタイムはこれの利点を実行します。

[!INCLUDE [help](../includes/get-help.md)]
