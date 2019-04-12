---
author: eliotcowley
title: IMLOperatorShapeInferenceContext.IsInputValid メソッド
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
- IMLOperatorShapeInferenceContext.IsInputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0bfda42be228353b3913ad15a93e6def9d9911d6
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473829"
---
# <a name="imloperatorshapeinferencecontextisinputvalid-method"></a>IMLOperatorShapeInferenceContext.IsInputValid メソッド

オペレーターへの入力が有効な場合に true を返します。 常に true を返します省略可能な入力と無効なインデックスを除く。

```cpp
bool IsInputValid(
    uint32_t inputIndex)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
