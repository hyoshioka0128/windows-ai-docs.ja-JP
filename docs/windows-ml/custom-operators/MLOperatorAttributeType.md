---
title: MLOperatorAttributeType 列挙型
description: 属性の型を指定します。 各属性の型は、対応する ONNX 型に一致します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorAttributeType
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttributeType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7c5a1c8cf538de134e8fecb336b7aee301a17565
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157547"
---
# <a name="mloperatorattributetype-enum"></a>MLOperatorAttributeType 列挙型

属性の型を指定します。 各属性の型は、対応する ONNX 型に一致します。

## <a name="fields"></a>フィールド

| 名前        | 値 | 説明                            |
|-------------|-------|----------------------------------------|
| 未定義。   | 0     | Undefined (未使用)。                    |
| Float       | 2     | 32ビットの浮動小数点。                 |
| Int         | 3     | 64ビット整数。                        |
| String      | 4     | 文字列値。                          |
| FloatArray  | 7     | 32ビット浮動小数点値の配列。 |
| IntArray    | 8     | 64ビット整数値の配列。        |
| StringArray | 9     | 文字列値の配列。                |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
