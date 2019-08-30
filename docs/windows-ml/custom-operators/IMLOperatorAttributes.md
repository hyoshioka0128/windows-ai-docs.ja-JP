---
title: IMLOperatorAttributes インターフェイス
description: 演算子を使用したモデルによって決定される、演算子の属性の値を表します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IMLOperatorAttributes
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ac15ec91bceeebb57c7cd7b45989aacfaebd69c9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157065"
---
# <a name="imloperatorattributes-interface"></a>IMLOperatorAttributes インターフェイス

演算子を使用したモデルによって決定される、演算子の属性の値を表します。 このインターフェイスは、カスタム演算子カーネルの実装、および形状と型の実装によって呼び出されます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetAttribute](IMLOperatorAttributes_GetAttribute.md) | 数値型の属性要素の値を取得します。 |
| [GetAttributeElementCount](IMLOperatorAttributes_GetAttributeElementCount.md) | 属性内の要素の数を取得します。 |
| [GetStringAttributeElement](IMLOperatorAttributes_GetStringAttributeElement.md) | 文字列型の属性要素の値を取得します。 |
| [GetStringAttributeElementLength](IMLOperatorAttributes_GetStringAttributeElementLength.md) | 文字列型の属性要素の長さを取得します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
