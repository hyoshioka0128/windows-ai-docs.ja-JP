---
author: eliotcowley
title: IMLOperatorKernelCreationContext.HasTensorShapeDescription メソッド
description: 演算子の端に入力と出力の図形の説明が接続されている場合は true を返しますを使用して照会することがあります**GetTensorShapeDescription**します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を HasTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.HasTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: ac854a1e6701055b99b3c79bfc8558887b20f279
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181694"
---
# <a name="imloperatorkernelcreationcontexthastensorshapedescription-method"></a>IMLOperatorKernelCreationContext.HasTensorShapeDescription メソッド

演算子の端に入力と出力の図形の説明が接続されている場合は true を返しますを使用して照会することがあります[IMLOperatorKernelCreationContext::GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md)します。 これは true を返しますを使用して、演算子が登録されていない限り、 [MLOperatorKernelOptions::AllowDynamicInputShapes](MLOperatorKernelOptions.md)フラグ。

```cpp
bool HasTensorShapeDescription()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
