---
title: ITensorNative インターフェイス
description: バイトまたは ID3D12Resource オブジェクトの配列として ITensor にアクセスできるようにします。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、ITensorNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9432f01613522bc2564eb9525c5b5943f9b464d4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157980"
---
# <a name="itensornative-interface"></a>ITensorNative インターフェイス

バイトまたは[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)オブジェクトの配列として[itensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)にアクセスできるようにします。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetBuffer](ITensorNative_GetBuffer.md) | 格納されているバッファーをバイト配列として取得します。 |
| [GetD3D12Resource](ITensorNative_GetD3D12Resource.md) | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)として格納されているバッファーを取得します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
