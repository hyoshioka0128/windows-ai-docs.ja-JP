---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.HasOutputShapeDescription メソッド
description: 使用して、出力の図形をクエリすることがある場合は true を返します**GetOutputTensorDimensionCount**と**GetOutputTensorShape**します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 927fc48cd6554d1d35292490892edb4534f90c82
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181854"
---
# <a name="imloperatortensorshapedescriptionhasoutputshapedescription-method"></a>IMLOperatorTensorShapeDescription.HasOutputShapeDescription メソッド

使用して、出力の図形をクエリすることがある場合は true を返します[IMLOperatorTensorShapeDescription::GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md)と[IMLOperatorTensorShapeDescription::GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md)します。 これは、カーネルが図形 inferrer に登録されている場合は true。

```cpp
bool HasOutputShapeDescription()
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
