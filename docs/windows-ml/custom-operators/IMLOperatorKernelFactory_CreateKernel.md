---
title: Imloperatorkernel ファクトリ. CreateKernel メソッド
description: 指定されたコンテキストオブジェクトに記述されているモデル内の演算子の使用法に関する情報を指定して、関連付けられている演算子カーネルのインスタンスを作成します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、CreateKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory.CreateKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fa1b909903d803bdc2e4b22c7edc92f5a4c6a288
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157570"
---
# <a name="imloperatorkernelfactorycreatekernel-method"></a>Imloperatorkernel ファクトリ. CreateKernel メソッド

指定されたコンテキストオブジェクトに記述されているモデル内の演算子の使用法に関する情報を指定して、関連付けられている演算子カーネルのインスタンスを作成します。

```cpp
void CreateKernel(
    IMLOperatorKernelCreationContext* context,
    _COM_Outptr_ IMLOperatorKernel** kernel)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
