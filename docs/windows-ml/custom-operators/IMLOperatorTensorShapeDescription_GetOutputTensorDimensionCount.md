---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount メソッド
description: 演算子の利用したテンソル出力の次元数を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetOutputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0f03d53fc9339930f9b42b5739230cba420b2e25
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181584"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensordimensioncount-method"></a>IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount メソッド

演算子の利用したテンソル出力の次元数を取得します。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
GetOutputTensorDimensionCount(
    uint32_t outputIndex, 
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
