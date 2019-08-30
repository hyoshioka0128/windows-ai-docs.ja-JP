---
title: IMLOperatorTypeInferrer インターフェイス
description: 演算子の出力エッジの型を推論するために型 inferrers によって実装されます。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IMLOperatorTypeInferrer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 5c72857c03c2d55fe0c194a8903199f76512135d
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156203"
---
# <a name="imloperatortypeinferrer-interface"></a>IMLOperatorTypeInferrer インターフェイス

演算子の出力エッジの型を推論するために型 inferrers によって実装されます。 [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md)構造体が出力の種類を決定&mdash;する方法を表現できない場合 (演算子の属性によってデータが決定される場合など)、カスタム演算子のスキーマを登録するときには、型 inferrers を指定する必要があります。その演算子の出力のいずれかの型。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [InferOutputTypes](IMLOperatorTypeInferrer_InferOutputTypes.md) | 演算子の出力エッジの型を推論するために呼び出されます。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
