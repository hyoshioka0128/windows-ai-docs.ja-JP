---
author: eliotcowley
title: IMLOperatorRegistry.RegisterOperatorSetSchema メソッド
description: 演算子のセットを構成するカスタム演算子のスキーマのセットを登録します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を RegisterOperatorSetSchema
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorSetSchema
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b10787c810a29076f6388d6b7755feec6bf2d7bb
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474699"
---
# <a name="imloperatorregistryregisteroperatorsetschema-method"></a>IMLOperatorRegistry.RegisterOperatorSetSchema メソッド

演算子のセットを構成するカスタム演算子のスキーマのセットを登録します。 演算子のセットでは、ONNX バージョン管理の設計に従います。 呼び出し元は、指定した構成基準のバージョンと内で指定されたバージョンが変更されたすべての演算子のスキーマを提供する必要があります*operatorSetId*します。 これは以前のバージョンのカーネルが新しい演算子セットのバージョンをインポートするモデルで使用されていることを防ぎます。 場合、型 inferrer を指定する必要があります、 [MLOperatorSchemaDescription](MLOperatorSchemaDescription.md)構造が出力の種類を決定する方法を表現することはできません。 図形 inferrer は、モデルの検証を有効にするのには必要に応じて提供されます。

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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
