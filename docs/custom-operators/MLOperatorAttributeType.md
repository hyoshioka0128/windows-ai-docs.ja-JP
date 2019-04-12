---
author: eliotcowley
title: MLOperatorAttributeType 列挙型
description: 属性の型を指定します。 各属性の型には、対応する ONNX 型数値と一致します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: b6f1fd8772ca183339ff03a672fcab69b1377c17
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474729"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
