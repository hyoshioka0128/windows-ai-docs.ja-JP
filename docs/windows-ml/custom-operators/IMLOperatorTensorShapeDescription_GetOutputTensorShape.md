---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.GetOutputTensorShape メソッド
description: 演算子の利用したテンソル出力の次元のサイズを取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetOutputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 56056d0eea93405d036d43ba4f8a8108ad67f0ba
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181514"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensorshape-method"></a>IMLOperatorTensorShapeDescription.GetOutputTensorShape メソッド

演算子の利用したテンソル出力の次元のサイズを取得します。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
GetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
