---
author: eliotcowley
title: IMLOperatorKernel.Compute メソッド
description: カーネルの出力を計算します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: c753516f3739b75292f5d52ce805d61faf168c3f
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181144"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
