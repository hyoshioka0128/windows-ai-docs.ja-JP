---
author: eliotcowley
title: IMLOperatorShapeInferenceContext.SetOutputTensorShape メソッド
description: 出力 tensor の推定の形状を設定します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 4e80f060dc544fd320a0aa2010c73731d108e3de
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474619"
---
# <a name="imloperatorshapeinferencecontextsetoutputtensorshape-method"></a>IMLOperatorShapeInferenceContext.SetOutputTensorShape メソッド

出力 tensor の推定の形状を設定します。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
void SetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    const uint32_t* dimensions)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
