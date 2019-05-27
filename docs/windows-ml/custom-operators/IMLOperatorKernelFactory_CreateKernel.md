---
author: eliotcowley
title: IMLOperatorKernelFactory.CreateKernel メソッド
description: 指定された、指定されたコンテキスト オブジェクトで説明されているモデル内の演算子の使用状況に関する情報に関連する演算子のカーネルのインスタンスを作成します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 8bf4b931267581e719d40e7166c59c8c813fe1ad
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180874"
---
# <a name="imloperatorkernelfactorycreatekernel-method"></a>IMLOperatorKernelFactory.CreateKernel メソッド

指定された、指定されたコンテキスト オブジェクトで説明されているモデル内の演算子の使用状況に関する情報に関連する演算子のカーネルのインスタンスを作成します。

```cpp
void CreateKernel(
    IMLOperatorKernelCreationContext* context,
    _COM_Outptr_ IMLOperatorKernel** kernel)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
