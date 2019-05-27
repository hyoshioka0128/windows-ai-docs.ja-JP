---
author: eliotcowley
title: IMLOperatorShapeInferrer インターフェイス
description: 演算子の出力 tensor エッジの図形を推論する図形 inferrers によって実装されます。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 41fefb1dfe04f99ec41ceae82cc247668b3f43c5
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180954"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
