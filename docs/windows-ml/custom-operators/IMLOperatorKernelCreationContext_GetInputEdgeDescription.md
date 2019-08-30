---
title: Imloperatorカーネルのコンテキスト。 IsOutputValid メソッド
description: 演算子の指定した入力エッジの説明を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetInputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.IsOutputValid
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: d6cba37f20e71fce7870ab38aec46d7af4d40a84
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157453"
---
# <a name="imloperatorkernelcreationcontextgetinputedgedescription-method"></a>ImloperatorGetInputEdgeDescription メソッド

演算子の指定した入力エッジの説明を取得します。

```cpp
void GetInputEdgeDescription(
    uint32_t inputIndex,
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
