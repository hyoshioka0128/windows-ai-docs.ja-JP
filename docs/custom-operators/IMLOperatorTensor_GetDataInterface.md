---
author: eliotcowley
title: IMLOperatorTensor.GetDataInterface メソッド
description: テンソルのインターフェイス ポインターを取得します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetDataInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fc434a519ce895b8cb5cc0e3bd2d96884e9bda0b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474399"
---
# <a name="imloperatortensorgetdatainterface-method"></a>IMLOperatorTensor.GetDataInterface メソッド

テンソルのインターフェイス ポインターを取得します。 可能性がある際に使用される[IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md)カーネルを使用して登録するために true を返す[MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md)します。 *DataInterface*オブジェクトのサポート、 [ID3D12Resource インターフェイス](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)GPU のバッファーとします。

```cpp
void GetDataInterface(
    _COM_Outptr_result_maybenull_ IUnknown** dataInterface)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
