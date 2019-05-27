---
author: eliotcowley
title: IMLOperatorKernelCreationContext.IsOutputValid method
description: オペレーターへの出力が有効な場合に true を返します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: b39a2c57a5deec11ff1b1d6cdfd133f982ef0f5b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180484"
---
# <a name="imloperatorkernelcreationcontextisoutputvalid-method"></a>IMLOperatorKernelCreationContext.IsOutputValid method

オペレーターへの出力が有効な場合に true を返します。 常に true を返します省略可能な出力を除く。

```cpp
bool IsOutputValid(uint32_t outputIndex)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
