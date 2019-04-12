---
author: eliotcowley
title: IMLOperatorTypeInferenceContext.IsOutputValid メソッド
description: オペレーターへの出力が有効な場合に true を返します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IsOutputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ec33aabec34cd9de96372934845e2dab39b55515
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474439"
---
# <a name="imloperatortypeinferencecontextisoutputvalid-method"></a>IMLOperatorTypeInferenceContext.IsOutputValid メソッド

オペレーターへの出力が有効な場合に true を返します。 常に true を返します省略可能な出力を除く。

```cpp
bool IsOutputValid(
    uint32_t outputIndex)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
