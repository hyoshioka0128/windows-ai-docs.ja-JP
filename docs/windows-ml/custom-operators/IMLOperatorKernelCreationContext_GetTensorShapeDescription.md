---
author: eliotcowley
title: IMLOperatorKernelCreationContext.GetTensorShapeDescription メソッド
description: 演算子の端に接続されている入力と出力の図形の説明を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 215dc45fd4ed2d7cb3a7ddd38af13a2e86bc3d5f
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181724"
---
# <a name="imloperatorkernelcreationcontextgettensorshapedescription-method"></a>IMLOperatorKernelCreationContext.GetTensorShapeDescription メソッド

演算子の端に接続されている入力と出力の図形の説明を取得します。

```cpp
void GetTensorShapeDescription(
    _COM_Outptr_ IMLOperatorTensorShapeDescription** shapeDescription)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
