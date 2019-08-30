---
title: MLOperatorSchemaEdgeTypeFormat 列挙型
description: 入力と出力のエッジの種類を記述する方法を指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorSchemaEdgeTypeFormat
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeTypeFormat
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 12afc60826f4a6f2ac4badbed4a876600544f81d
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157671"
---
# <a name="mloperatorschemaedgetypeformat-enum"></a>MLOperatorSchemaEdgeTypeFormat 列挙型

入力と出力のエッジの種類を記述する方法を指定します。 これは、カスタムの演算子スキーマを定義するときに[MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)内で使用されます。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| EdgeDescription | 0 | この型は[MLOperatorEdgeDescription](MLOperatorEdgeDescription.md)を使用して定義されます。 |
| Label | 1 | この型は、ONNX operator スキーマとして構築された型文字列によって定義されます。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
