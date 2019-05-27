---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount メソッド
description: 演算子の利用したテンソル入力の次元数を取得します。
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
- IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0f2d26e85ef38a2d7be6cbdd460be02b415ff3cc
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181764"
---
# <a name="imloperatortensorshapedescriptiongetinputtensordimensioncount-method"></a>IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount メソッド

演算子の利用したテンソル入力の次元数を取得します。 指定したインデックス位置にある入力を利用したテンソルでない場合は、エラーを返します。

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex, 
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
