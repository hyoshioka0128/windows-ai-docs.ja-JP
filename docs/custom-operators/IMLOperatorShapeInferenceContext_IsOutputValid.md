---
author: eliotcowley
title: IMLOperatorShapeInferenceContext.IsOutputValid メソッド
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
- IMLOperatorShapeInferenceContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: a761249ce973b228664cb6dccb828ce72692868d
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474329"
---
# <a name="imloperatorshapeinferencecontextisoutputvalid-method"></a>IMLOperatorShapeInferenceContext.IsOutputValid メソッド

オペレーターへの出力が有効な場合に true を返します。 常に true を返します省略可能な出力は、無効なインデックスを除く。

```cpp
bool IsOutputValid(
    uint32_t outputIndex)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
