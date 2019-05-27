---
author: eliotcowley
title: IMLOperatorTypeInferenceContext.IsInputValid メソッド
description: オペレーターへの入力が有効な場合に true を返します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IsInputValid
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: eebc570860a9098f93da017136000f52149b7664
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180244"
---
# <a name="imloperatortypeinferencecontextisinputvalid-method"></a>IMLOperatorTypeInferenceContext.IsInputValid メソッド

オペレーターへの入力が有効な場合に true を返します。 常に true を返します省略可能な入力を除く。

```cpp
bool IsInputValid(
    uint32_t inputIndex)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
