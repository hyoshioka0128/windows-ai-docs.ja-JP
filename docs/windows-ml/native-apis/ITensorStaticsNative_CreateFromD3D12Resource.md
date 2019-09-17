---
title: ITensorStaticsNative メソッド
description: ユーザー指定の ID3D12Resource から、TensorInt32Bit オブジェクト () を作成します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、CreateFromD3D12Resource
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative.CreateFromD3D12Resource
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 251c45c0f444affc2c154de056e4916a5ba1ba93
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156416"
---
# <a name="itensorstaticsnativecreatefromd3d12resource-method"></a>ITensorStaticsNative メソッド

ユーザー指定の [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource) から、 [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)[オブジェクト (](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)) を作成します。

```cpp
HRESULT CreateFromD3D12Resource(
    ID3D12Resource *value,
    [size_is(shapeCount)] __int64 *shape,
    int shapeCount,
    [out] IUnknown ** result);
```

## <a name="parameters"></a>パラメーター

| 名前 | 型 | 説明 |
|------|------|-------------|
| value | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)* | **ID3D12Resource**を作成する元の。 |
| オート | **__int64**\* | 整理されたの形。 |
| スナップショット | **int** | 表示されているの次元の数。 |
| 結果 | [IUnknown](https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown)** | 結果として生成された。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="examples"></a>使用例

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

* [カスタムのカスタマイズのサンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
