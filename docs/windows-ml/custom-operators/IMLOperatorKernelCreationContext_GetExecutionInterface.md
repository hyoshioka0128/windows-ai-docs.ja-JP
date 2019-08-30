---
title: Imloperator、GetExecutionInterface メソッド
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
- IMLOperatorKernelCreationContext.GetExecutionInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8cec5c1da7fbd4c0aa211f9c6fb7f020eb46c6cd
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157377"
---
# <a name="imloperatorkernelcreationcontextgetexecutioninterface-method"></a>Imloperator、GetExecutionInterface メソッド

カーネルの種類によってサポートされるインターフェイスが異なるオブジェクトを返します。 [Mloperatorexecutiontype:: Cpu](MLOperatorExecutionType.md)に登録されているカーネルの場合、 *executionobject*は**nullptr**に設定されます。 **Mloperatorexecutiontype::D 3D12**に登録されているカーネルの場合、 *Executionobject*は[ID3D12GraphicsCommandList](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)インターフェイスをサポートします。

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
