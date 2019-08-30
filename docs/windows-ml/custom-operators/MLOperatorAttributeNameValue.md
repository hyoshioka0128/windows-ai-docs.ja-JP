---
title: MLOperatorAttributeNameValue 構造体
description: カスタム演算子の属性の名前と値を指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorAttributeNameValue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttributeNameValue
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 04fd271cea818db29ff8f6402eb37dfb537d4ea3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157951"
---
# <a name="mloperatorattributenamevalue-struct"></a>MLOperatorAttributeNameValue 構造体

カスタム演算子の属性の名前と値を指定します。 これは、カスタム演算子カーネルとカスタム演算子スキーマを登録するときに使用されます。

## <a name="fields"></a>フィールド

| 名前       | 型                    | 説明 |
|------------|-------------------------|-------------|
| 浮かん     | **const float***            | 32ビット浮動小数点値。 Type フィールドが**Mloperatorattributetype:: Float**または**Mloperatorattributetype:: FloatArray**の場合に使用します。 |
| int       | **const int64_t***          | 64ビットの整数値。 Type フィールドが**Mloperatorattributetype:: Int**または**Mloperatorattributetype:: intarray**の場合に使用されます。 |
| NAME       | **const char***             | NULL で終わる UTF-8 文字列で、関連付けられている演算子の種類の属性の名前を表します。 |
| 確保   | **const void***             |             |
| strings    | **const char\*定数***      | NULL で終わる UTF-8 文字列値です。 Type フィールドが**Mloperatorattributetype:: String**または**Mloperatorattributetype:: stringarray**の場合に使用されます。 |
| type       | [MLOperatorAttributeType](MLOperatorAttributeType.md) | 関連付けられている演算子の種類の属性の型。 |
| valueCount | **uint32_t**                | 属性値の要素の数。 これは、配列型の属性を除き、1である必要があります。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
