---
title: Imloperatortenantsordescription インターフェイス
description: オペレーターの入力および出力のセットを表します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Imloperatorの説明
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 17f8c02a79d71bb6265e4c9d2061014db2454fcb
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157833"
---
# <a name="imloperatortensorshapedescription-interface"></a>Imloperatortenantsordescription インターフェイス

オペレーターの入力および出力のセットを表します。 このインターフェイスは、カーネルを作成するために登録されたファクトリオブジェクトによって呼び出されます。 対応するカーネルが[MLOperatorKernelOptions:: AllowDynamicInputShapes](MLOperatorKernelOptions.md)フラグを使用して登録されている場合を除き、これらのファクトリオブジェクトで使用できます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetInputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetInputTensorDimensionCount.md) | 入力されたオペレーターの入力の次元数を取得します。 |
| [GetInputTensorShape](IMLOperatorTensorShapeDescription_GetInputTensorShape.md) | 入力された演算子の大きさのサイズを取得します。 |
| [GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md) | 操作のすべての出力の次元数を取得します。 |
| [GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md) | 操作のすべての出力のサイズを取得します。 |
| [HasOutputShapeDescription](IMLOperatorTensorShapeDescription_HasOutputShapeDescription.md) | **Getoutputに**よって出力図形がクエリされる場合は true を返します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
