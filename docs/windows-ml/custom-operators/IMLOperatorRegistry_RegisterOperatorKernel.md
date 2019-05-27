---
author: eliotcowley
title: IMLOperatorRegistry.RegisterOperatorKernel メソッド
description: カスタム演算子のカーネルを登録します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: ee74cda25980361adc8c435e903dd8ddbc0717cf
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181704"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
