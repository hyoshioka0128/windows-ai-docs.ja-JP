---
title: IMLOperatorKernel. Compute メソッド
description: カーネルの出力を計算します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Compute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel.Compute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d29b07d8e66e0666db29cfb66adde15191393eb4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157583"
---
# <a name="imloperatorkernelcompute-method"></a>IMLOperatorKernel. Compute メソッド

カーネルの出力を計算します。 このメソッドの実装は、スレッドセーフである必要があります。 カーネルの同じインスタンスは、異なるスレッドで同時に計算される場合があります。

```cpp
void Compute(
    IMLOperatorKernelContext* context)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
