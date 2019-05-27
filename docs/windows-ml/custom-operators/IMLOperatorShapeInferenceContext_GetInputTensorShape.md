---
author: eliotcowley
title: IMLOperatorShapeInferenceContext.GetInputTensorShape メソッド
description: 演算子の入力に利用したテンソルの次元のサイズを取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetInputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext.GetInputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fec4996bcc8f7b4272334bd9a5c57a38f205dc17
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181004"
---
# <a name="imloperatorshapeinferencecontextgetinputtensorshape-method"></a>IMLOperatorShapeInferenceContext.GetInputTensorShape メソッド

演算子の入力に利用したテンソルの次元のサイズを取得します。 指定したインデックス位置にある入力を利用したテンソルでない場合は、エラーを返します。

```cpp
void GetInputTensorShape(
    uint32_t inputIndex,
    uint32_t dimensionCount,
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
