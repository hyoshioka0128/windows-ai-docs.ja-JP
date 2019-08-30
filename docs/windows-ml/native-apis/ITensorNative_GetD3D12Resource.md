---
title: ITensorNative メソッド
description: ID3D12Resource として格納されているバッファーを取得します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、GetD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9384311d5060df0cf0e4542fd202bdd20cfb73e0
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156470"
---
# <a name="itensornativegetd3d12resource-method"></a>ITensorNative メソッド

[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)として格納されているバッファーを取得します。

```cpp
HRESULT GetD3D12Resource(
    [out] ID3D12Resource ** result);
```

## <a name="parameters"></a>パラメーター

| 名前 | 型 | 説明 |
|------|------|-------------|
| 結果 | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)** | **ID3D12Resource**としての、格納されていないバッファー。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
