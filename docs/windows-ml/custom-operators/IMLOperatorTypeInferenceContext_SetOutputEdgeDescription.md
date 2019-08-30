---
title: IMLOperatorTypeInferenceContext SetOutputEdgeDescription メソッド
description: 出力エッジの推定される型を設定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、SetOutputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext.SetOutputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ca3248c16d449a0a21521e00883446f1fd70e47e
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157926"
---
# <a name="imloperatortypeinferencecontextsetoutputedgedescription-method"></a>IMLOperatorTypeInferenceContext SetOutputEdgeDescription メソッド

出力エッジの推定される型を設定します。

```cpp
void SetOutputEdgeDescription(
    uint32_t outputIndex,
    const MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
