---
title: Imloperatorカーネルコンテキスト。 Allocate一時データメソッド
description: '**Imloperatorkernel:: Compute**の呼び出し中に、中間メモリとして使用できる一時データを割り当てます。'
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Allocate一時データ
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.AllocateTemporaryData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ccc7e98f928ab77d7265c647165774e9fb74312a
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157244"
---
# <a name="imloperatorkernelcontextallocatetemporarydata-method"></a>Imloperatorカーネルコンテキスト。 Allocate一時データメソッド

[Imloperatorkernel:: Compute](IMLOperatorKernel_Compute.md)の呼び出し中に、中間メモリとして使用できる一時データを割り当てます。 これは、 [Mloperatorexecutiontype::D 3D12](MLOperatorExecutionType.md)を使用して登録されたカーネルによって使用される場合があります。 データオブジェクトは、 [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)インターフェイスをサポートします。これは GPU バッファーです。

```cpp
void AllocateTemporaryData(
    size_t size,
    _COM_Outptr_ IUnknown** data)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
