---
author: eliotcowley
title: IMLOperatorKernelCreationContext.IsInputValid method
description: オペレーターへの入力が有効な場合に true を返します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IsInputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 9790098f3e3e69236b75ba00d30022bdd1e375b8
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474779"
---
# <a name="imloperatorkernelcreationcontextisinputvalid-method"></a>IMLOperatorKernelCreationContext.IsInputValid method

オペレーターへの入力が有効な場合に true を返します。 常に true を返します省略可能な入力を除く。

```cpp
bool IsInputValid(uint32_t inputIndex)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
