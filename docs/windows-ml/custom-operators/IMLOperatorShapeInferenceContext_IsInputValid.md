---
title: IMLOperatorShapeInferenceContext IsInputValid メソッド
description: 演算子への入力が有効な場合は true を返します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IsInputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 4520b1d8a4621dc7d837cfa1e19c4fb170ebf6c3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156978"
---
# <a name="imloperatorshapeinferencecontextisinputvalid-method"></a>IMLOperatorShapeInferenceContext IsInputValid メソッド

演算子への入力が有効な場合は true を返します。 これは、オプションの入力および無効なインデックスを除き、常に true を返します。

```cpp
bool IsInputValid(
    uint32_t inputIndex)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
