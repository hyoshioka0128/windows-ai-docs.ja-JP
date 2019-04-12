---
author: eliotcowley
title: ITensorNative.GetD3D12Resource メソッド
description: ID3D12Resource として利用したテンソル バッファーを取得します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、GetD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 5c694e4ba199dc604534b88a5f60a91cb90d016a
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475039"
---
# <a name="itensornativegetd3d12resource-method"></a>ITensorNative.GetD3D12Resource メソッド

として利用したテンソル バッファーを取得、 [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)します。

```cpp
HRESULT GetD3D12Resource(
    [out] ID3D12Resource ** result);
```

## <a name="parameters"></a>パラメーター

| 名前 | 種類 | 説明 |
|------|------|-------------|
| 結果 | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)** | として利用したテンソル バッファー、 **ID3D12Resource**します。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../includes/get-help.md)]
