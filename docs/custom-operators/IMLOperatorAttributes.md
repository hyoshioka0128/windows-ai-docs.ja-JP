---
author: eliotcowley
title: IMLOperatorAttributes インターフェイス
description: 演算子を使用して、モデルによって決定される、演算子の属性の値を表します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorAttributes
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0099e28cd0f542fc59880f299e7e874f088c4fb5
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474939"
---
# <a name="imloperatorattributes-interface"></a>IMLOperatorAttributes インターフェイス

演算子を使用して、モデルによって決定される、演算子の属性の値を表します。 このインターフェイスは、カーネルではカスタム演算子の実装によって、図形と種類 inferrers の実装によって呼び出されます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetAttribute](IMLOperatorAttributes_GetAttribute.md) | 数値型の属性要素の値を取得します。 |
| [GetAttributeElementCount](IMLOperatorAttributes_GetAttributeElementCount.md) | 属性内の要素数を取得します。 |
| [GetStringAttributeElement](IMLOperatorAttributes_GetStringAttributeElement.md) | 文字列型の属性要素の値を取得します。 |
| [GetStringAttributeElementLength](IMLOperatorAttributes_GetStringAttributeElementLength.md) | 文字列型の属性要素の長さを取得します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
