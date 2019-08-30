---
title: ITensorNative メソッド
description: 格納されているバッファーをバイト配列として取得します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、GetBuffer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetBuffer
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: f20f49ad4f16905ab53bccc3d3316d41f615b041
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156493"
---
# <a name="itensornativegetbuffer-method"></a>ITensorNative メソッド

格納されているバッファーをバイト配列として取得します。

```cpp
HRESULT GetBuffer(
    [out, size_is(, *capacity)] BYTE **value,
    [out] UINT32 *capacity);
```

## <a name="parameters"></a>パラメーター

| 名前 | 型 | 説明 |
|------|------|-------------|
| value | **バイト**\*\* | 格納されているバッファー。 |
| capacity | **UINT32**\* | バッファーの容量。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="examples"></a>使用例

```cpp
TensorFloat SoftwareBitmapToSoftwareTensor(SoftwareBitmap softwareBitmap)
{
    // 1. Get access to the buffer of softwareBitmap
    BYTE* pData = nullptr;
    UINT32 size = 0;
    BitmapBuffer spBitmapBuffer(softwareBitmap.LockBuffer(BitmapBufferAccessMode::Read));
    winrt::Windows::Foundation::IMemoryBufferReference reference = spBitmapBuffer.CreateReference();
    auto spByteAccess = reference.as<::Windows::Foundation::IMemoryBufferByteAccess>();
    CHECK_HRESULT(spByteAccess->GetBuffer(&pData, &size));

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
