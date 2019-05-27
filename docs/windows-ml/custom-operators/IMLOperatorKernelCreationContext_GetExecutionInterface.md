---
author: eliotcowley
title: IMLOperatorKernelCreationContext.GetExecutionInterface メソッド
description: カーネルの種類に基づいて、サポートされているインターフェイスが異なるオブジェクトを返します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetExecutionInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d410e8ee9129cf09230bc46a3c1bb03d6431674e
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180564"
---
# <a name="imloperatorkernelcreationcontextgetexecutioninterface-method"></a>IMLOperatorKernelCreationContext.GetExecutionInterface メソッド

カーネルの種類に基づいて、サポートされているインターフェイスが異なるオブジェクトを返します。 登録されているカーネルの[MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md)、 *executionObject*に設定されます**nullptr**します。 登録されているカーネルの**MLOperatorExecutionType::D3D12**、 *executionObject*サポートは、 [ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)インターフェイス。

```cpp
void GetExecutionInterface(
    _COM_Outptr_result_maybenull_ IUnknown** executionObject)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
