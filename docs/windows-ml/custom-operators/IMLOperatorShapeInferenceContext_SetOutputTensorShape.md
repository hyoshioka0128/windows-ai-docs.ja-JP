---
author: eliotcowley
title: IMLOperatorShapeInferenceContext.SetOutputTensorShape メソッド
description: 出力 tensor の推定の形状を設定します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を SetOutputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.SetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 40013b7248050afaad6d8f59cebd7a0074b14a9a
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181024"
---
# <a name="imloperatorshapeinferencecontextsetoutputtensorshape-method"></a>IMLOperatorShapeInferenceContext.SetOutputTensorShape メソッド

出力 tensor の推定の形状を設定します。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
void SetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    const uint32_t* dimensions)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
