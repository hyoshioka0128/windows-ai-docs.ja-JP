---
author: eliotcowley
title: MLCreateOperatorRegistry 関数
description: インスタンスを作成します**IMLOperatorRegistry**カスタム演算子のカーネルとカスタム演算子のスキーマを登録するこれを使用することがあります。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: a94b68f559e4a959a0a39b196f26f49923326c30
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181484"
---
# <a name="mlcreateoperatorregistry-function"></a>MLCreateOperatorRegistry 関数

インスタンスを作成します[IMLOperatorRegistry](IMLOperatorRegistry.md)カスタム演算子のカーネルとカスタム演算子のスキーマを登録するこれを使用することがあります。

```cpp
HRESULT MLCreateOperatorRegistry(
    _COM_Outptr_ IMLOperatorRegistry** registry)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
