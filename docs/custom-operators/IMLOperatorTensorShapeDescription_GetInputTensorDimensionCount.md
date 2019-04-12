---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount メソッド
description: 演算子の利用したテンソル入力の次元数を取得します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: b3d7b39f635b830f2d7d031a3b889c916b90c6bf
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474259"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
