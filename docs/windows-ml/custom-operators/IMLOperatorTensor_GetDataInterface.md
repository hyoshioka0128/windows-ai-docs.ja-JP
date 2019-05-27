---
author: eliotcowley
title: IMLOperatorTensor.GetDataInterface メソッド
description: テンソルのインターフェイス ポインターを取得します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: c57f09e7c041343f67587892757754d78baa43ad
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180604"
---
# <a name="imloperatortensorgetdatainterface-method"></a>IMLOperatorTensor.GetDataInterface メソッド

テンソルのインターフェイス ポインターを取得します。 可能性がある際に使用される[IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md)カーネルを使用して登録するために true を返す[MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md)します。 *DataInterface*オブジェクトのサポート、 [ID3D12Resource インターフェイス](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)GPU のバッファーとします。

```cpp
void GetDataInterface(
    _COM_Outptr_result_maybenull_ IUnknown** dataInterface)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
