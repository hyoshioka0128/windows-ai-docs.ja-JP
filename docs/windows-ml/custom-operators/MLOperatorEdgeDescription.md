---
author: eliotcowley
title: MLOperatorEdgeDescription 構造体
description: 演算子のエッジを入力または出力のプロパティを指定します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 68c6c65e1b01ed4bc72e22c39882322e264d6597
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181434"
---
# <a name="mloperatoredgedescription-struct"></a>MLOperatorEdgeDescription 構造体

演算子のエッジを入力または出力のプロパティを指定します。

## <a name="fields"></a>フィールド

| 名前           | 種類                     | 説明           |
|----------------|--------------------------|-----------------------|
| edgeType       | [MLOperatorEdgeType](MLOperatorEdgeType.md)       | エッジの種類。 |
| 予約されています       | **uint64_t**                 |                       |
| tensorDataType | [MLOperatorTensorDataType](MLOperatorTensorDataType.md) | 利用したテンソルのデータ型。 ときに使用される**edgeType**に設定されている**Tensor**します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
