---
title: Imloperator@ Context. GetExecutionInterface メソッド
description: カーネルの種類によってサポートされるインターフェイスが異なるオブジェクトを返します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetExecutionInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fa342999351dd2c1a218ffd086bcd09a1ec9405f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157289"
---
# <a name="imloperatorkernelcontextgetexecutioninterface-method"></a>Imloperator@ Context. GetExecutionInterface メソッド

カーネルの種類によってサポートされるインターフェイスが異なるオブジェクトを返します。 [Mloperatorexecutiontype:: Cpu](MLOperatorExecutionType.md)に登録されているカーネルの場合、 *executionobject*は**nullptr**に設定されます。 **Mloperatorexecutiontype::D 3D12**に登録されているカーネルの場合、 *Executionobject*は[ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)インターフェイスをサポートします。 これは、カーネルインスタンスの作成時に[Imloperatorkernel の context:: GetExecutionInterface](IMLOperatorKernelCreationContext_GetExecutionInterface.md)に提供されたものとは異なるオブジェクトである可能性があります。

```cpp
void GetExecutionInterface(
    _COM_Outptr_result_maybenull_ IUnknown** executionObject)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
