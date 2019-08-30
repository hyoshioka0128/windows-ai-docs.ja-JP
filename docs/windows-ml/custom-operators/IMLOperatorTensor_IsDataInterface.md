---
title: Imloperator(IsDataInterface) メソッド
description: すべての内容がインターフェイス型で表されるか、またはバイトアドレス可能なメモリで表されるかを示します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IsDataInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.IsDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c3a44e9e7c7402bfb83d71c6a51aa1d2a21226c7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157896"
---
# <a name="imloperatortensorisdatainterface-method"></a>Imloperator(IsDataInterface) メソッド

すべての内容がインターフェイス型で表されるか、またはバイトアドレス可能なメモリで表されるかを示します。 これは、カーネルが[Mloperatorexecutiontype::D 3D12](MLOperatorExecutionType.md)を使用して登録されている場合に true を返します。

```cpp
bool IsDataInterface()
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
