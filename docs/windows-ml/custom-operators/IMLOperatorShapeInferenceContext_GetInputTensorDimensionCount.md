---
title: IMLOperatorShapeInferenceContext Count メソッドを呼び出します。
description: 操作のすべての出力の次元数を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Getinputの Sordimensioncount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8d191d379045918422c62c80eeac2d8573931860
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157745"
---
# <a name="imloperatorshapeinferencecontextgetinputtensordimensioncount-method"></a>IMLOperatorShapeInferenceContext Count メソッドを呼び出します。

操作のすべての出力の次元数を取得します。

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex,
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
