---
author: eliotcowley
title: IMLOperatorAttributes インターフェイス
description: 演算子を使用して、モデルによって決定される、演算子の属性の値を表します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: c04adcd91142d7b3ec0bdae5011a9293d5c19e17
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180994"
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

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
