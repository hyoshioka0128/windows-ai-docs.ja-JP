---
author: eliotcowley
title: MLOperatorTensorDataType 列挙型
description: 利用したテンソルのデータ型を指定します。 データの種類ごとには、対応する ONNX 型数値と一致します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: b35f643ed43317e6124224e7334f4af02c4f9e93
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474639"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
