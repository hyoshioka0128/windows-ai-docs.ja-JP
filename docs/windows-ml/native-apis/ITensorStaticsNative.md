---
title: ITensorStaticsNative インターフェイス
description: ID3D12Resource を使用して ITensor オブジェクトを作成できるようにするファクトリメソッドへのアクセスを提供します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、ITensorStaticsNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 1b828c1611535d4c5c41a1380b12664959b1dc28
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156435"
---
# <a name="itensorstaticsnative-interface"></a>ITensorStaticsNative インターフェイス

[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)を使用して[itensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)オブジェクトを作成できるようにするファクトリメソッドへのアクセスを提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateFromD3D12Resource](ITensorStaticsNative_CreateFromD3D12Resource.md) | ユーザー指定の [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) から、 [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)[オブジェクト (](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)) を作成します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
