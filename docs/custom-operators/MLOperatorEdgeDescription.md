---
author: eliotcowley
title: MLOperatorEdgeDescription 構造体
description: 演算子のエッジを入力または出力のプロパティを指定します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8d578d29b5e24e7e64ab1d3f704503fb0f46eeb1
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474379"
---
# <a name="mloperatoredgedescription-struct"></a>MLOperatorEdgeDescription 構造体

演算子のエッジを入力または出力のプロパティを指定します。

## <a name="fields"></a>フィールド

| 名前           | 種類                     | 説明           |
|----------------|--------------------------|-----------------------|
| edgeType       | [MLOperatorEdgeType](MLOperatorEdgeType.md)       | エッジの種類。 |
| 予約されています       | **uint64_t**                 |                       |
| tensorDataType | [MLOperatorTensorDataType](MLOperatorTensorDataType.md) | 利用したテンソルのデータ型。 ときに使用される**edgeType**に設定されている**Tensor**します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
