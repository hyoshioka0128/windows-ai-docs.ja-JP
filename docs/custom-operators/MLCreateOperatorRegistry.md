---
author: eliotcowley
title: MLCreateOperatorRegistry 関数
description: インスタンスを作成します**IMLOperatorRegistry**カスタム演算子のカーネルとカスタム演算子のスキーマを登録するこれを使用することがあります。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLCreateOperatorRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLCreateOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d0cc289af9b7746dbb9015cf6108995467f79cd2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473979"
---
# <a name="mlcreateoperatorregistry-function"></a>MLCreateOperatorRegistry 関数

インスタンスを作成します[IMLOperatorRegistry](IMLOperatorRegistry.md)カスタム演算子のカーネルとカスタム演算子のスキーマを登録するこれを使用することがあります。

```cpp
HRESULT MLCreateOperatorRegistry(
    _COM_Outptr_ IMLOperatorRegistry** registry)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
