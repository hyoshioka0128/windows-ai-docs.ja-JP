---
title: ILearningModelDeviceFactoryNative CreateFromD3D12CommandQueue メソッド
description: ユーザー指定の ID3D12CommandQueue に対して推論を実行する LearningModelDevice を作成します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、CreateFromD3D12CommandQueue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: bdc255f22d0bafe43d9f8ba9470615a5ce15a5c9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156565"
---
# <a name="ilearningmodeldevicefactorynativecreatefromd3d12commandqueue-method"></a>ILearningModelDeviceFactoryNative CreateFromD3D12CommandQueue メソッド

ユーザー指定の[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)に対して推論を実行する[LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)を作成します。

```cpp
HRESULT CreateFromD3D12CommandQueue(
    ID3D12CommandQueue * value,
    [out] IUnknown ** result);
```

## <a name="parameters"></a>パラメーター

| 名前 | 型 | 説明 |
|------|------|-------------|
| value | [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)* | **LearningModelDevice**を実行する**ID3D12CommandQueue** 。 |
| 結果 | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | 作成される**LearningModelDevice** 。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="examples"></a>使用例

```cpp
 // 1. create the d3d device.
com_ptr<ID3D12Device> pD3D12Device = nullptr;
CHECK_HRESULT(D3D12CreateDevice(
    nullptr,
    D3D_FEATURE_LEVEL::D3D_FEATURE_LEVEL_11_0,
    __uuidof(ID3D12Device),
    reinterpret_cast<void**>(&pD3D12Device)));

// 2. create the command queue.
com_ptr<ID3D12CommandQueue> dxQueue = nullptr;
D3D12_COMMAND_QUEUE_DESC commandQueueDesc = {};
commandQueueDesc.Type = D3D12_COMMAND_LIST_TYPE_DIRECT;
CHECK_HRESULT(pD3D12Device->CreateCommandQueue(
    &commandQueueDesc,
    __uuidof(ID3D12CommandQueue),
    reinterpret_cast<void**>(&dxQueue)));
com_ptr<ILearningModelDeviceFactoryNative> devicefactory =
    get_activation_factory<LearningModelDevice, ILearningModelDeviceFactoryNative>();
com_ptr<::IUnknown> spUnk;
CHECK_HRESULT(devicefactory->CreateFromD3D12CommandQueue(dxQueue.get(), spUnk.put()));
```

## <a name="see-also"></a>関連項目

* [カスタムのカスタマイズのサンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
