---
title: IMLOperatorShapeInferenceContext メソッド
description: 演算子への出力が有効な場合は true を返します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IsOutputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8dd8ef2987fc5400c66fa549f173e2f6fded6744
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157767"
---
# <a name="imloperatorshapeinferencecontextisoutputvalid-method"></a>IMLOperatorShapeInferenceContext メソッド

演算子への出力が有効な場合は true を返します。 省略可能な出力と無効なインデックスの場合を除き、常に true を返します。

```cpp
bool IsOutputValid(
    uint32_t outputIndex)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
