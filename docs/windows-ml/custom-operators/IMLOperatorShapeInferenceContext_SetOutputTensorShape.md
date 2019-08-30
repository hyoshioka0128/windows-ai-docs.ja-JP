---
title: IMLOperatorShapeInferenceContext メソッドを呼び出すことができます。
description: 出力の推論された形状を設定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Setoutput整理 Sorshape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.SetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f4500e42f3ee6c8f47f555d8e7eb7d50c8a929ab
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157605"
---
# <a name="imloperatorshapeinferencecontextsetoutputtensorshape-method"></a>IMLOperatorShapeInferenceContext メソッドを呼び出すことができます。

出力の推論された形状を設定します。 指定されたインデックスの出力が、まだ存在しない場合はエラーを返します。

```cpp
void SetOutputTensorShape(
    uint32_t outputIndex,
    uint32_t dimensionCount,
    const uint32_t* dimensions)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
