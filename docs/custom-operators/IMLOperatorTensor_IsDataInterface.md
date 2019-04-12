---
author: eliotcowley
title: IMLOperatorTensor.IsDataInterface メソッド
description: かどうか、利用したテンソルの内容はインターフェイスの型、またはバイトのアドレス指定可能なメモリによって表されます。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IsDataInterface
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.IsDataInterface
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 410f74d1518229813b9504bc4f78d076a68ef6f5
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474039"
---
# <a name="imloperatortensorisdatainterface-method"></a>IMLOperatorTensor.IsDataInterface メソッド

かどうか、利用したテンソルの内容はインターフェイスの型、またはバイトのアドレス指定可能なメモリによって表されます。 これは true を返しますを使用してカーネルが登録される[MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md)します。

```cpp
bool IsDataInterface()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
