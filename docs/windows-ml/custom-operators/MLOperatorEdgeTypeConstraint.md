---
title: MLOperatorEdgeTypeConstraint 構造体
description: カスタム演算子カーネルおよびスキーマでサポートされているエッジの種類に対する制約を指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorEdgeTypeConstraint
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeTypeConstraint
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d2f1b6132f744eece3d25e0cb9732e7c196ee2cf
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157725"
---
# <a name="mloperatoredgetypeconstraint-struct"></a>MLOperatorEdgeTypeConstraint 構造体

カスタム演算子カーネルおよびスキーマでサポートされているエッジの種類に対する制約を指定します。 指定された型ラベル文字列は、同じ演算子の ONNX 仕様の型ラベルに対応します。 カスタムスキーマの場合は、演算子のスキーマを登録するときに、 [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)内で指定された型ラベルに対応します。

## <a name="fields"></a>フィールド

| 名前 | 型 | 説明 |
|------|------|-------------|
| allowedTypeCount | **uint32_t** | |
| Allowedtypes.xml | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md)* | 制約に許可されている型のセット。 |
| typeLabel | **char*** | 制約が定義されている型のラベル。 これは、ONNX operator スキーマで構成されます。 たとえば、"T" のようになります。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
