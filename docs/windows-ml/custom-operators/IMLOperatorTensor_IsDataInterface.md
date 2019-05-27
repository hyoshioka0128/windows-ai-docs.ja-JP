---
author: eliotcowley
title: IMLOperatorTensor.IsDataInterface メソッド
description: かどうか、利用したテンソルの内容はインターフェイスの型、またはバイトのアドレス指定可能なメモリによって表されます。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 475311c07442660f83c0a9336468d6e9d2dbed00
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180294"
---
# <a name="imloperatortensorisdatainterface-method"></a>IMLOperatorTensor.IsDataInterface メソッド

かどうか、利用したテンソルの内容はインターフェイスの型、またはバイトのアドレス指定可能なメモリによって表されます。 これは true を返しますを使用してカーネルが登録される[MLOperatorExecutionType::D3D12](MLOperatorExecutionType.md)します。

```cpp
bool IsDataInterface()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
