---
author: eliotcowley
title: MLOperatorAttribute 構造体
description: カスタム演算子の属性のプロパティと名前を指定します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 6d5b9aeb6cc20a9aae48971a1c0735ef5b4c7049
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182084"
---
# <a name="mloperatorattribute-struct"></a>MLOperatorAttribute 構造体

カスタム演算子の属性のプロパティと名前を指定します。 これは、カスタム演算子のカーネルとカスタム演算子のスキーマを登録するときに使用されます。

## <a name="fields"></a>フィールド

| 名前     | 種類                    | 説明 |
|----------|-------------------------|-------------|
| name     | **Char***                   | NULL で終わる utf-8 文字列に関連する演算子の型の属性の名前を表します。 |
| required | **bool**                    | かどうか、属性は、関連付けられている演算子の種類を使用して任意のモデルに必要です。 |
| type     | [MLOperatorAttributeType](MLOperatorAttributeType.md) | 関連付けられている演算子の種類の属性の型。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
