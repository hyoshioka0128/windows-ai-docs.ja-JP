---
author: eliotcowley
title: MLOperatorAttribute 構造体
description: カスタム演算子の属性のプロパティと名前を指定します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: eaf1265d545c34833b67a6695bc2496a1258b0c4
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474799"
---
# <a name="mloperatorattribute-struct"></a>MLOperatorAttribute 構造体

カスタム演算子の属性のプロパティと名前を指定します。 これは、カスタム演算子のカーネルとカスタム演算子のスキーマを登録するときに使用されます。

## <a name="fields"></a>フィールド

| 名前     | 種類                    | 説明 |
|----------|-------------------------|-------------|
| name     | **Char***                   | NULL で終わる utf-8 文字列に関連する演算子の型の属性の名前を表します。 |
| required | **bool**                    | かどうか、属性は、関連付けられている演算子の種類を使用して任意のモデルに必要です。 |
| type     | [MLOperatorAttributeType](MLOperatorAttributeType.md) | 関連付けられている演算子の種類の属性の型。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
