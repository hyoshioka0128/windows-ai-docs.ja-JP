---
title: MLOperatorEdgeDescription 構造体
description: 演算子の入力または出力エッジのプロパティを指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 76fde8dcb9c8ddcb89de272cf478c8b56e8ebeaa
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156823"
---
# <a name="mloperatoredgedescription-struct"></a>MLOperatorEdgeDescription 構造体

演算子の入力または出力エッジのプロパティを指定します。

## <a name="fields"></a>フィールド

| 名前           | 型                     | 説明           |
|----------------|--------------------------|-----------------------|
| edgeType       | [MLOperatorEdgeType](MLOperatorEdgeType.md)       | エッジの種類。 |
| 確保       | **uint64_t**                 |                       |
| すべてのデータ型 | [MLOperatorTensorDataType](MLOperatorTensorDataType.md) | のデータ型。 EdgeType が " " に設定されている場合に使用します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
