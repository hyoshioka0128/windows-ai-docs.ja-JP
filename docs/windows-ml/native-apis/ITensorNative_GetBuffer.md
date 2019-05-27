---
author: eliotcowley
title: ITensorNative.GetBuffer メソッド
description: バイト配列として利用したテンソルのバッファーを取得します。
ms.author: elcowle
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、GetBuffer
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative.GetBuffer
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: fa00f6300516da0dee20ce85a6bd7bfc3cb6ed07
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180114"
---
# <a name="itensornativegetbuffer-method"></a>ITensorNative.GetBuffer メソッド

バイト配列として利用したテンソルのバッファーを取得します。

```cpp
HRESULT GetBuffer(
    [out, size_is(, *capacity)] BYTE **value, 
    [out] UINT32 *capacity);
```

## <a name="parameters"></a>パラメーター

| 名前 | 種類 | 説明 |
|------|------|-------------|
| value | **バイト**\*\* | 利用したテンソルのバッファー。 |
| 容量 | **UINT32**\* | バッファーの容量。 |

## <a name="returns"></a>戻り値

**HRESULT**操作の結果。

## <a name="examples"></a>例

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

* [カスタム Tensorization サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization)

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
