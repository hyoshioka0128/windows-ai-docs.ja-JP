---
author: eliotcowley
title: MLOperatorAttributeNameValue struct
description: カスタム演算子の属性の値と名前を指定します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorAttributeNameValue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttributeNameValue
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: eedef4a8eeca543a6ab6dfaa1d11feb58a5b3045
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474679"
---
# <a name="mloperatorattributenamevalue-struct"></a>MLOperatorAttributeNameValue struct

カスタム演算子の属性の値と名前を指定します。 これは、カスタム演算子のカーネルとカスタム演算子のスキーマを登録するときに使用されます。

## <a name="fields"></a>フィールド

| 名前       | 種類                    | 説明 |
|------------|-------------------------|-------------|
| 浮動小数点数     | **const float***            | 32 ビット浮動小数点のポイント値。 [種類] フィールドが場合に使用**MLOperatorAttributeType::Float**または**MLOperatorAttributeType::FloatArray**します。 |
| 整数       | **const int64_t***          | 64 ビット整数値。 [種類] フィールドが場合に使用**MLOperatorAttributeType::Int**または**MLOperatorAttributeType::IntArray**します。 |
| name       | **const char***             | NULL で終わる utf-8 文字列に関連する演算子の型の属性の名前を表します。 |
| 予約されています   | **const void***             |             |
| 文字列    | **const char\*定数***      | NULL で終わる utf-8 文字列値です。 [種類] フィールドが場合に使用**MLOperatorAttributeType::String**または**MLOperatorAttributeType::StringArray**します。 |
| type       | [MLOperatorAttributeType](MLOperatorAttributeType.md) | 関連付けられている演算子の種類の属性の型。 |
| valueCount | **uint32_t**                | 属性値内の要素の数。 これは、配列型の属性を除いて、1 でなければなりません。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
