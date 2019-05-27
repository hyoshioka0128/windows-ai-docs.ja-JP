---
author: eliotcowley
title: ITensorNative.GetD3D12Resource メソッド
description: ID3D12Resource として利用したテンソル バッファーを取得します。
ms.author: elcowle
ms.date: 4/2/2019
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
ms.openlocfilehash: 6d1b6284118a09cc2b0d1d1a2da7438385f581c7
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180174"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
