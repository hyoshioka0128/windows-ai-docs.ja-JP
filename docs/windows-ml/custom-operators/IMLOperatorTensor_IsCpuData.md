---
title: Imloperatorall/Iscpu Data メソッド
description: この値によって使用されるメモリが CPU でアドレス指定可能かどうかを示します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Iscpu データ
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.IsCpuData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 9e68cb31f7c88bb782e45b38f557cec66512ee88
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157879"
---
# <a name="imloperatortensoriscpudata-method"></a>Imloperatorall/Iscpu Data メソッド

この値によって使用されるメモリが CPU でアドレス指定可能かどうかを示します。 これは、カーネルが[Mloperatorexecutiontype:: Cpu](MLOperatorExecutionType.md)を使用して登録されている場合に当てはまります。

```cpp
bool IsCpuData()
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
