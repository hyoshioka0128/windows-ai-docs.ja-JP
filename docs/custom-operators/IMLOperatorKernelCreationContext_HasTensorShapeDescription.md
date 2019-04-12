---
author: eliotcowley
title: IMLOperatorKernelCreationContext.HasTensorShapeDescription メソッド
description: 演算子の端に入力と出力の図形の説明が接続されている場合は true を返しますを使用して照会することがあります**GetTensorShapeDescription**します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: cc72e6ab688d72cf124cf4b795f236ddc7554048
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475059"
---
# <a name="imloperatorkernelcreationcontexthastensorshapedescription-method"></a>IMLOperatorKernelCreationContext.HasTensorShapeDescription メソッド

演算子の端に入力と出力の図形の説明が接続されている場合は true を返しますを使用して照会することがあります[IMLOperatorKernelCreationContext::GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md)します。 これは true を返しますを使用して、演算子が登録されていない限り、 [MLOperatorKernelOptions::AllowDynamicInputShapes](MLOperatorKernelOptions.md)フラグ。

```cpp
bool HasTensorShapeDescription()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
