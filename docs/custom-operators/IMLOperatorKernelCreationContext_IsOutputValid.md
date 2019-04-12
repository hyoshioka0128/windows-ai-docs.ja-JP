---
author: eliotcowley
title: IMLOperatorKernelCreationContext.IsOutputValid method
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
- IMLOperatorKernelCreationContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1f07330e9047057651b171555fc1a57e49c6e1c6
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474239"
---
# <a name="imloperatorkernelcreationcontextisoutputvalid-method"></a>IMLOperatorKernelCreationContext.IsOutputValid method

オペレーターへの出力が有効な場合に true を返します。 常に true を返します省略可能な出力を除く。

```cpp
bool IsOutputValid(uint32_t outputIndex)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
