---
author: eliotcowley
title: IMLOperatorTensor.IsCpuData メソッド
description: テンソルによって使用されるメモリが CPU を指定できるかどうかを示します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 41bf7d78013dd6f8445e8e671974ec5745e99502
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180384"
---
# <a name="imloperatortensoriscpudata-method"></a>IMLOperatorTensor.IsCpuData メソッド

テンソルによって使用されるメモリが CPU を指定できるかどうかを示します。 これは、カーネルを使用して登録されている場合は true。 [MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md)します。

```cpp
bool IsCpuData()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
