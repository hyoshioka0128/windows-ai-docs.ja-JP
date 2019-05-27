---
author: eliotcowley
title: IMLOperatorRegistry.RegisterOperatorSetSchema メソッド
description: 演算子のセットを構成するカスタム演算子のスキーマのセットを登録します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: bb7778112cbc54f4bf13150f4a132b17f3b68681
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180694"
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

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
