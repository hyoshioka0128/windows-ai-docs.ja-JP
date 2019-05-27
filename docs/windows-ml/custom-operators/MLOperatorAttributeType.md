---
author: eliotcowley
title: MLOperatorAttributeType 列挙型
description: 属性の型を指定します。 各属性の型には、対応する ONNX 型数値と一致します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorAttributeType
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttributeType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 09e847c7ebfce894249ef06b778cdb5ec3039a79
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182054"
---
# <a name="mloperatorattributetype-enum"></a>MLOperatorAttributeType 列挙型

属性の型を指定します。 各属性の型には、対応する ONNX 型数値と一致します。

## <a name="fields"></a>フィールド

| 名前        | 値 | 説明                            |
|-------------|-------|----------------------------------------|
| 未定義   | 0     | (未使用) 定義されていません。                    |
| Float       | 2     | 32 ビット浮動小数点数。                 |
| 整数         | 3     | 64 ビット整数。                        |
| String      | 4     | 文字列値です。                          |
| FloatArray  | 7     | 32 ビット浮動小数点値の配列。 |
| Intarray に割り当て    | 8     | 64 ビット整数値の配列。        |
| StringArray | 9     | 文字列値の配列。                |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
