---
title: ILearningModelDeviceFactoryNative インターフェイス
description: ID3D12CommandQueue を使用して ILearningModelDevice オブジェクトを作成できるようにするファクトリメソッドへのアクセスを提供します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、ILearningModelDeviceFactoryNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 0f6fdf7a32c768690a47dc3028b8a01adffce056
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156574"
---
# <a name="ilearningmodeldevicefactorynative-interface"></a>ILearningModelDeviceFactoryNative インターフェイス

[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)を使用して[ILearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)オブジェクトを作成できるようにするファクトリメソッドへのアクセスを提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateFromD3D12CommandQueue](ILearningModelDeviceFactoryNative_CreateFromD3D12CommandQueue.md) | ユーザー指定の[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)に対して推論を実行する[LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)を作成します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
