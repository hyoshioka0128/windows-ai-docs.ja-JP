---
author: eliotcowley
title: IMLOperatorKernel.Compute メソッド
description: カーネルの出力を計算します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、カスタム演算子は、コンピューティングします。
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel.Compute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bcdf39f14e84872624a2c20cfcef437c80010b76
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474749"
---
# <a name="imloperatorkernelcompute-method"></a>IMLOperatorKernel.Compute メソッド

カーネルの出力を計算します。 このメソッドの実装は、スレッド セーフであるはずです。 カーネルの同じインスタンスを異なるスレッドで同時に計算する可能性があります。

```cpp
void Compute(
    IMLOperatorKernelContext* context)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
