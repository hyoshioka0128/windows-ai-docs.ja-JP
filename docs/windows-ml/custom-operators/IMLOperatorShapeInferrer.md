---
title: Imloperator図形 Inferrer インターフェイス
description: 図形形式で実装され、演算子の出力の形状を推定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Imloperator図形 Inferrer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 64917ecf3cf490ccb98db86bc670189acbb43c78
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157773"
---
# <a name="imloperatorshapeinferrer-interface"></a>Imloperator図形 Inferrer インターフェイス

図形形式で実装され、演算子の出力の形状を推定します。 カスタム演算子カーネルを登録してパフォーマンスを向上させ、カーネルが作成および計算されたときにその出力 tensors の形状に対してクエリを実行できるようにする場合は、形状を指定できます。 カスタム演算子スキーマを登録するときに、モデルの検証を改善するために、図形を指定することもできます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [InferOutputShapes](IMLOperatorShapeInferrer_InferOutputShapes.md) | 演算子の出力エッジの形状を推論するために呼び出されます。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
