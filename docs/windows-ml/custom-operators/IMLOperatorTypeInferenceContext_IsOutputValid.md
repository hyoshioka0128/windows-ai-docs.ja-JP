---
author: eliotcowley
title: IMLOperatorTypeInferenceContext.IsOutputValid メソッド
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
- IMLOperatorTypeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0635371ebafba764100670ffd7a09c207104780a
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180504"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
