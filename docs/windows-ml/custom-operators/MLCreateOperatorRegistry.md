---
title: Mlcreateのレジストリ関数
description: カスタム演算子カーネルとカスタムの演算子スキーマを登録するために使用できる**Imloperatorregistry**のインスタンスを作成します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Mlcreateoperators レジストリ
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLCreateOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7c758f30476bb306628c1e63b787a61b1301ef8d
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156089"
---
# <a name="mlcreateoperatorregistry-function"></a>Mlcreateのレジストリ関数

カスタム演算子カーネルとカスタムの演算子スキーマを登録するために使用できる[Imloperatorregistry](IMLOperatorRegistry.md)のインスタンスを作成します。

```cpp
HRESULT MLCreateOperatorRegistry(
    _COM_Outptr_ IMLOperatorRegistry** registry)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
