---
title: MLOperatorTensorDataType 列挙型
description: のデータ型を指定します。 それぞれのデータ型は、対応する ONNX 型に一致します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Mloperatortenantdatatype
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorTensorDataType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1726fbdbbe834a8f5f3d4c98d3c27bedf5612da4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156723"
---
# <a name="mloperatortensordatatype-enum"></a>MLOperatorTensorDataType 列挙型

のデータ型を指定します。 それぞれのデータ型は、対応する ONNX 型に一致します。

## <a name="fields"></a>フィールド

| 名前       | 値 | 説明                             |
|------------|-------|-----------------------------------------|
| 未定義。  | 0     | Undefined (未使用)。                     |
| Float      | 1     | IEEE 32 ビットの浮動小数点。             |
| UInt8      | 2     | 8ビット符号なし整数。                 |
| Int8       | 3     | 8ビット符号付き整数。                   |
| UInt16     | 4     | 16ビット符号なし整数。                |
| Int16      | 5     | 16ビット符号付き整数。                  |
| Int32      | 6     | 32ビット符号付き整数。                  |
| Int64      | 7     | 64ビット符号付き整数。                  |
| String     | 8     | 文字列 (サポートされていません)。                   |
| Bool       | 9     | 8ビットのブール値。 0および1以外の値の場合、未定義の動作が発生します。 |
| Float16    | 10    | IEEE 16 ビット浮動小数点。             |
| Double     | 11    | 64ビット倍精度浮動小数点。 |
| UInt32     | 12    | 32ビット符号なし整数。                |
| UInt64     | 13    | 64ビット符号なし整数。                |
| Complex64  | 14    | 64-bit 複合型 (サポートされていません)。      |
| Complex128 | 15    | 128-bit 複合型 (サポートされていません)。     |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
