---
author: eliotcowley
title: IMLOperatorKernelFactory.CreateKernel メソッド
description: 指定された、指定されたコンテキスト オブジェクトで説明されているモデル内の演算子の使用状況に関する情報に関連する演算子のカーネルのインスタンスを作成します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を CreateKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory.CreateKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b26d810b3501318ad7c94fe95c94803af629a979
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474179"
---
# <a name="imloperatorkernelfactorycreatekernel-method"></a>IMLOperatorKernelFactory.CreateKernel メソッド

指定された、指定されたコンテキスト オブジェクトで説明されているモデル内の演算子の使用状況に関する情報に関連する演算子のカーネルのインスタンスを作成します。

```cpp
void CreateKernel(
    IMLOperatorKernelCreationContext* context,
    _COM_Outptr_ IMLOperatorKernel** kernel)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
