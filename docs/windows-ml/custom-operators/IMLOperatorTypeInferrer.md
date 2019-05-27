---
author: eliotcowley
title: IMLOperatorTypeInferrer インターフェイス
description: 型 inferrers によって実装される、演算子の型を推論する出力のエッジ。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorTypeInferrer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferrer
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: dd979f3a40b5b9f921a14a3a8acf70386591e4ee
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182114"
---
# <a name="imloperatortypeinferrer-interface"></a>IMLOperatorTypeInferrer インターフェイス

型 inferrers によって実装される、演算子の型を推論する出力のエッジ。 場合は、カスタム演算子のスキーマを登録するときに、型 inferrers を提供する必要があります、 [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md)構造は出力の種類を決定する方法を表現できない&mdash;ときの属性の例については、演算子は、その演算子の出力のいずれかのデータ型を決定します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [InferOutputTypes](IMLOperatorTypeInferrer_InferOutputTypes.md) | 演算子の出力のエッジの型を推論と呼ばれます。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
