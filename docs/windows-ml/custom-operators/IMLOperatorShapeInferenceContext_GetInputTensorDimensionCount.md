---
author: eliotcowley
title: IMLOperatorShapeInferenceContext.GetInputTensorDimensionCount メソッド
description: 演算子の利用したテンソル出力の次元数を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetInputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7d9b2f19f59b56131f3e8cd00b893c576e815546
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180424"
---
# <a name="imloperatorshapeinferencecontextgetinputtensordimensioncount-method"></a>IMLOperatorShapeInferenceContext.GetInputTensorDimensionCount メソッド

演算子の利用したテンソル出力の次元数を取得します。

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex,
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
