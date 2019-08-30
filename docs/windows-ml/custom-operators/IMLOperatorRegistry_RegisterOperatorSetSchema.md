---
title: IMLOperatorRegistry。 Registerの Setschema メソッド
description: 演算子セットを構成するカスタムの演算子スキーマのセットを登録します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Registeroperators Setschema
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorSetSchema
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f8746ecd7c58b759f7c46115759f4f977c1578a8
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157630"
---
# <a name="imloperatorregistryregisteroperatorsetschema-method"></a>IMLOperatorRegistry。 Registerの Setschema メソッド

演算子セットを構成するカスタムの演算子スキーマのセットを登録します。 演算子セットは、ONNX バージョン管理の設計に従います。 呼び出し元は、指定された基準バージョンと、operator *setid*内で指定されたバージョンの間で変更されたすべての演算子に対してスキーマを提供する必要があります。 これにより、新しいバージョンの演算子セットをインポートするモデルで、以前のバージョンのカーネルが使用されるのを防ぐことができます。 [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md)構造体が出力の種類を決定する方法を表現できない場合は、型 inferrer を指定する必要があります。 モデルの検証を有効にするために、必要に応じて図形の形式を指定することもできます。

```cpp
void RegisterOperatorSetSchema(
    const MLOperatorSetId* operatorSetId,
    int32_t baselineVersion,
    _In_reads_opt_(schemaCount) const MLOperatorSchemaDescription* const* schema,
    uint32_t schemaCount,
    _In_opt_ IMLOperatorTypeInferrer* typeInferrer,
    _In_opt_ IMLOperatorShapeInferrer* shapeInferrer)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
