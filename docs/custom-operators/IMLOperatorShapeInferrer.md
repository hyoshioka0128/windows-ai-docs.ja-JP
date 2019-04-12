---
author: eliotcowley
title: IMLOperatorShapeInferrer インターフェイス
description: 演算子の出力 tensor エッジの図形を推論する図形 inferrers によって実装されます。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorShapeInferrer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7c887e5ebe2b7574136555910fb0613a5d2cbf2d
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474509"
---
# <a name="imloperatorshapeinferrer-interface"></a>IMLOperatorShapeInferrer インターフェイス

演算子の出力 tensor エッジの図形を推論する図形 inferrers によって実装されます。 パフォーマンスを向上させるために作成され、計算時に、その出力 tensors の形状を照会するカーネルを有効にして、カスタム演算子カーネルを登録するときに、図形 inferrers を指定することがあります。 図形 inferrers はモデルの検証を向上させるためにカスタム演算子のスキーマを登録するときにも提供されます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [InferOutputShapes](IMLOperatorShapeInferrer_InferOutputShapes.md) | 演算子の出力のエッジの図形を推論と呼ばれます。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
