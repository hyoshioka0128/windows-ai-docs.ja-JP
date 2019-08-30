---
title: IMLOperatorTypeInferenceContext メソッド
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
- IMLOperatorTypeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c112e4f1ad3e09ae4a02f1cc7a5b38fa90413911
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156066"
---
# <a name="imloperatortypeinferencecontextisoutputvalid-method"></a>IMLOperatorTypeInferenceContext メソッド

演算子への出力が有効な場合は true を返します。 これは、省略可能な出力を除き、常に true を返します。

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
