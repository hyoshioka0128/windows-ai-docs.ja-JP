---
author: eliotcowley
title: IMLOperatorTensor.IsCpuData メソッド
description: テンソルによって使用されるメモリが CPU を指定できるかどうかを示します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IsCpuData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.IsCpuData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3323f8422f69fc2a826a785820703b69e5e27b43
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474159"
---
# <a name="imloperatortensoriscpudata-method"></a>IMLOperatorTensor.IsCpuData メソッド

テンソルによって使用されるメモリが CPU を指定できるかどうかを示します。 これは、カーネルを使用して登録されている場合は true。 [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md)します。

```cpp
bool IsCpuData()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
