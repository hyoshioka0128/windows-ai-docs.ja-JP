---
author: eliotcowley
title: IMLOperatorRegistry.RegisterOperatorKernel メソッド
description: カスタム演算子のカーネルを登録します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を RegisterOperatorKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d98ff79c38020cb4ad94496ffd8f6933c31a44bf
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474289"
---
# <a name="imloperatorregistryregisteroperatorkernel-method"></a>IMLOperatorRegistry.RegisterOperatorKernel メソッド

カスタム演算子のカーネルを登録します。 図形 inferrer は必要に応じて提供されます。  これはパフォーマンスが向上でき、カーネルが作成され、計算時に、その出力 tensors の形状を照会します。

```cpp
void RegisterOperatorKernel(
    const MLOperatorKernelDescription* operatorKernel,
    IMLOperatorKernelFactory* operatorKernelFactory,
    _In_opt_ IMLOperatorShapeInferrer* shapeInferrer)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
