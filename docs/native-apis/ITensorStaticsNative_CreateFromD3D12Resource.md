---
author: eliotcowley
title: ITensorStaticsNative.CreateFromD3D12Resource メソッド
description: ユーザーが指定した ID3D12Resource から (TensorFloat、TensorInt32Bit) を利用したテンソル オブジェクトを作成します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、CreateFromD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative.CreateFromD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9fdcbb444f872f8fc8292c41e9253325f1e73176
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474979"
---
# <a name="itensorstaticsnativecreatefromd3d12resource-method"></a>ITensorStaticsNative.CreateFromD3D12Resource メソッド

利用したテンソル オブジェクトを作成します ([TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)、 [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)) からユーザーが指定した[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)します。

```cpp
HRESULT CreateFromD3D12Resource(
    ID3D12Resource *value, 
    [size_is(shapeCount)] __int64 *shape, 
    int shapeCount, 
    [out] IUnknown ** result);
```

## <a name="parameters"></a>パラメーター

| 名前 | 種類 | 説明 |
|------|------|-------------|
| value | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)* | **ID3D12Resource**テンソルの作成に使用します。 |
| 図形 | **__int64**\* | テンソルの形状。 |
| shapeCount | **int** | テンソルの次元数。 |
| 結果 | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | 結果として得られる tensor します。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="examples"></a>例

```cpp
TensorFloat SoftwareBitmapToDX12Tensor(SoftwareBitmap softwareBitmap)
{
    // ...
    
    // GPU tensorize
    com_ptr<ITensorStaticsNative> tensorfactory = get_activation_factory<TensorFloat, ITensorStaticsNative>();
    com_ptr<::IUnknown> spUnkTensor;
    TensorFloat input1imagetensor(nullptr);
    int64_t shapes[4] = { 1,3, softwareBitmap.PixelWidth(), softwareBitmap.PixelHeight() };
    CHECK_HRESULT(tensorfactory->CreateFromD3D12Resource(pGPUResource.get(), shapes, 4, spUnkTensor.put()));
    spUnkTensor.try_as(input1imagetensor);

    // ...
}
```

## <a name="see-also"></a>関連項目

* [カスタム Tensorization サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../includes/get-help.md)]