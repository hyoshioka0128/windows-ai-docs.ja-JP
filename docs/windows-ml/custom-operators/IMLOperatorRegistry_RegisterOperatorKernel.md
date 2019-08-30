---
title: IMLOperatorRegistry. Register演算子カーネルメソッド
description: カスタムの演算子カーネルを登録します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Registeroperators カーネル
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry.RegisterOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 86dd68896d6855295915d7b37ef1e88e933c7ccd
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157639"
---
# <a name="imloperatorregistryregisteroperatorkernel-method"></a>IMLOperatorRegistry. Register演算子カーネルメソッド

カスタムの演算子カーネルを登録します。 必要に応じて、形状を指定することもできます。  これにより、パフォーマンスが向上し、カーネルが作成および計算されたときに、その出力 tensors の形状を照会できるようになります。

```cpp
void RegisterOperatorKernel(
    const MLOperatorKernelDescription* operatorKernel,
    IMLOperatorKernelFactory* operatorKernelFactory,
    _In_opt_ IMLOperatorShapeInferrer* shapeInferrer)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
