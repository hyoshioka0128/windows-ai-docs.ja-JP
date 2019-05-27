---
author: eliotcowley
title: ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue メソッド
description: ユーザーが指定した ID3D12CommandQueue で推論を実行する LearningModelDevice を作成します。
ms.author: elcowle
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、CreateFromD3D12CommandQueue
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 07aa84b1dbfd8143af70caa8ef9758c5ef1867d7
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180144"
---
# <a name="ilearningmodeldevicefactorynativecreatefromd3d12commandqueue-method"></a>ILearningModelDeviceFactoryNative.CreateFromD3D12CommandQueue メソッド

作成、 [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)推論を実行するユーザー指定の[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)します。

```cpp
HRESULT CreateFromD3D12CommandQueue(
    ID3D12CommandQueue * value, 
    [out] IUnknown ** result);
```

## <a name="parameters"></a>パラメーター

| 名前 | 種類 | 説明 |
|------|------|-------------|
| value | [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)* | **ID3D12CommandQueue**を**LearningModelDevice**に対して実行されます。 |
| 結果 | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | **LearningModelDevice**を作成します。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="examples"></a>例

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

* [カスタム Tensorization サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
