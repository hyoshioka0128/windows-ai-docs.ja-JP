---
author: eliotcowley
title: MLOperatorTensorDataType 列挙型
description: 利用したテンソルのデータ型を指定します。 データの種類ごとには、対応する ONNX 型数値と一致します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorTensorDataType
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorTensorDataType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ee7a8ecd9af0b5b67f57cbb7d09b8517d583829b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181274"
---
# <a name="mloperatortensordatatype-enum"></a>MLOperatorTensorDataType 列挙型

利用したテンソルのデータ型を指定します。 データの種類ごとには、対応する ONNX 型数値と一致します。

## <a name="fields"></a>フィールド

| 名前       | 値 | 説明                             |
|------------|-------|-----------------------------------------|
| 未定義  | 0     | (未使用) 定義されていません。                     |
| Float      | 1     | 32 ビット浮動小数点数 IEEE。             |
| UInt8      | 2     | 8 ビット符号なし整数。                 |
| Int8       | 3     | 8 ビット符号付き整数。                   |
| UInt16     | 4     | 16 ビット符号なし整数。                |
| int16      | 5     | 16 ビット符号付き整数。                  |
| Int32      | 6     | 32 ビット符号付き整数。                  |
| Int64      | 7     | 64 ビット符号付き整数。                  |
| String     | 8     | (サポートされていない) 文字列。                   |
| Bool       | 9     | 8 ビットのブール値。 未定義の動作で 0 と 1 つの結果以外の値。 |
| Float16    | 10    | IEEE 16 ビットの浮動小数点。             |
| Double     | 11    | 64 ビット倍精度浮動小数点。 |
| UInt32     | 12    | 32 ビット符号なし整数。                |
| UInt64     | 13    | 64 ビット符号なし整数。                |
| Complex64  | 14    | 64 ビットの複合型が (サポート対象外)。      |
| Complex128 | 15    | 128 ビットの複合型が (サポート対象外)。     |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
