---
author: eliotcowley
title: IMLOperatorKernelCreationContext.GetTensorShapeDescription メソッド
description: 演算子の端に接続されている入力と出力の図形の説明を取得します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 7832d281a2c5b0c5699840e4c431a4bf87886a39
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474499"
---
# <a name="imloperatorkernelcreationcontextgettensorshapedescription-method"></a>IMLOperatorKernelCreationContext.GetTensorShapeDescription メソッド

演算子の端に接続されている入力と出力の図形の説明を取得します。

```cpp
void GetTensorShapeDescription(
    _COM_Outptr_ IMLOperatorTensorShapeDescription** shapeDescription)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
