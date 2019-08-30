---
title: Imloperator(GetDataInterface) メソッド
description: 既存ののインターフェイスポインターを取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetDataInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 84903d4a3be68494de5352ee7368056b9ac1b6f8
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157863"
---
# <a name="imloperatortensorgetdatainterface-method"></a>Imloperator(GetDataInterface) メソッド

既存ののインターフェイスポインターを取得します。 これは、 [Imloperatorthe:: IsDataInterface](IMLOperatorTensor_IsDataInterface.md)が true を返す場合に使用できます。これは、カーネルが[Mloperatorexecutiontype::D 3d12](MLOperatorExecutionType.md)を使用して登録されたためです。 *Datainterface*オブジェクトは、 [ID3D12Resource インターフェイス](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)をサポートします。これは GPU バッファーです。

```cpp
void GetDataInterface(
    _COM_Outptr_result_maybenull_ IUnknown** dataInterface)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
