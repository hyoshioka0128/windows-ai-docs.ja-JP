---
author: eliotcowley
title: IMLOperatorKernelCreationContext.IsOutputValid method
description: 演算子の指定した入力のエッジの説明を取得します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetInputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: cd1fe4363e52a1739ec9da0d978386ce194f7bfb
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474479"
---
# <a name="imloperatorkernelcreationcontextgetinputedgedescription-method"></a>IMLOperatorKernelCreationContext.GetInputEdgeDescription メソッド

演算子の指定した入力のエッジの説明を取得します。

```cpp
void GetInputEdgeDescription(
    uint32_t inputIndex, 
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]