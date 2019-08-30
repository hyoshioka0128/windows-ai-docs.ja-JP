---
title: MLOperatorSetId 構造体
description: オペレーターセットの id を指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorSetId
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSetId
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3288a9b6057db9349295d9d20f83f0ab93229c90
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156759"
---
# <a name="mloperatorsetid-struct"></a>MLOperatorSetId 構造体

オペレーターセットの id を指定します。

## <a name="fields"></a>フィールド

| 名前 | 型 | 説明 |
|------|------|-------------|
| domain | **const char*** | 演算子のドメイン (例、"ai.onnx.ml")、または ONNX ドメインの空の文字列。 |
| version | **int32_t** | オペレータードメインのバージョン。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
