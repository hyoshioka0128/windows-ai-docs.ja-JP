---
author: eliotcowley
title: IMLOperatorKernelContext.AllocateTemporaryData メソッド
description: 呼び出しの間の中間メモリとして使用できる一時的なデータを割り当てます**IMLOperatorKernel::Compute**します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を AllocateTemporaryData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.AllocateTemporaryData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b0b6668f89c8c5afb15d714d7ebbc3a5be679280
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474809"
---
# <a name="imloperatorkernelcontextallocatetemporarydata-method"></a>IMLOperatorKernelContext.AllocateTemporaryData メソッド

呼び出しの間の中間メモリとして使用できる一時的なデータを割り当てます[IMLOperatorKernel::Compute](IMLOperatorKernel_Compute.md)します。 これを使用して登録されているカーネルで使用できる[MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md)します。 データ オブジェクト サポート、 [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)インターフェイス、および GPU のバッファーします。

```cpp
void AllocateTemporaryData(
    size_t size, 
    _COM_Outptr_ IUnknown** data)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
