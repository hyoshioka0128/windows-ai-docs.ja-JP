---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.HasOutputShapeDescription メソッド
description: 使用して、出力の図形をクエリすることがある場合は true を返します**GetOutputTensorDimensionCount**と**GetOutputTensorShape**します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を HasOutputShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.HasOutputShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 963f5dbb6358ff0f04b653be8dfbfab691c591c7
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474389"
---
# <a name="imloperatortensorshapedescriptionhasoutputshapedescription-method"></a>IMLOperatorTensorShapeDescription.HasOutputShapeDescription メソッド

使用して、出力の図形をクエリすることがある場合は true を返します[IMLOperatorTensorShapeDescription::GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md)と[IMLOperatorTensorShapeDescription::GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md)します。 これは、カーネルが図形 inferrer に登録されている場合は true。

```cpp
bool HasOutputShapeDescription()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
