---
author: eliotcowley
title: IMLOperatorKernelCreationContext.GetOutputEdgeDescription メソッド
description: 演算子の指定した出力のエッジの説明を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetOutputEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetOutputEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 99719e1a8692ee962d566a6f38c6dc004166e138
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181564"
---
# <a name="imloperatorkernelcreationcontextgetoutputedgedescription-method"></a>IMLOperatorKernelCreationContext.GetOutputEdgeDescription メソッド

演算子の指定した出力のエッジの説明を取得します。

```cpp
void GetOutputEdgeDescription(
    uint32_t outputIndex, 
    _Out_ MLOperatorEdgeDescription* edgeDescription)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
