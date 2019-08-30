---
title: Imloperator(GetData) メソッド
description: は、その後、またはに対して、バイトでアドレス指定可能なメモリへのポインターを返します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 150def2eb9f33e0ffdcb1c77e6429862f4697705
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157886"
---
# <a name="imloperatortensorgetdata-method"></a>Imloperator(GetData) メソッド

は、その後、またはに対して、バイトでアドレス指定可能なメモリへのポインターを返します。 これは、 [Imloperatorthe:: IsDataInterface](IMLOperatorTensor_IsDataInterface.md)が false を返す場合に使用できます。これは、カーネルが[Mloperatorexecutiontype:: Cpu](MLOperatorExecutionType.md)を使用して登録されたためです。 データサイズは、整理された形から派生します。 メモリに完全にパックされています。

```cpp
void* GetData()
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
