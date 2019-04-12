---
author: eliotcowley
title: IMLOperatorKernelCreationContext.GetExecutionInterface メソッド
description: カーネルの種類に基づいて、サポートされているインターフェイスが異なるオブジェクトを返します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 3111f983491ff4effe09727bf5220a36f9498fd0
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474899"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
