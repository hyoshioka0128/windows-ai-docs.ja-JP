---
author: eliotcowley
title: IMLOperatorTypeInferrer インターフェイス
description: 型 inferrers によって実装される、演算子の型を推論する出力のエッジ。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 70fe73eecb38e41be5a73e34a3fbf6390aecf99f
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474549"
---
# <a name="imloperatortypeinferrer-interface"></a>IMLOperatorTypeInferrer インターフェイス

型 inferrers によって実装される、演算子の型を推論する出力のエッジ。 場合は、カスタム演算子のスキーマを登録するときに、型 inferrers を提供する必要があります、 [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md)構造は出力の種類を決定する方法を表現できない&mdash;ときの属性の例については、演算子は、その演算子の出力のいずれかのデータ型を決定します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [InferOutputTypes](IMLOperatorTypeInferrer_InferOutputTypes.md) | 演算子の出力のエッジの型を推論と呼ばれます。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
