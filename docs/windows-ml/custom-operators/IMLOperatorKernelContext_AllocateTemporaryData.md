---
author: eliotcowley
title: IMLOperatorKernelContext.AllocateTemporaryData メソッド
description: 呼び出しの間の中間メモリとして使用できる一時的なデータを割り当てます**IMLOperatorKernel::Compute**します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 0c1ffe8d50052e37e109f869346228031c35bb36
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180674"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
