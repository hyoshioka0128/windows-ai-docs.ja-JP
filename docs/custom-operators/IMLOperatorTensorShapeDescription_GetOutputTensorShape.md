---
author: eliotcowley
title: IMLOperatorTensorShapeDescription.GetOutputTensorShape メソッド
description: 演算子の利用したテンソル出力の次元のサイズを取得します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetOutputTensorShape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: e0ee2405831213e8ee537bf3e8a1960acf328bc1
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474029"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensorshape-method"></a>IMLOperatorTensorShapeDescription.GetOutputTensorShape メソッド

演算子の利用したテンソル出力の次元のサイズを取得します。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
GetOutputTensorShape(
    uint32_t outputIndex, 
    uint32_t dimensionCount, 
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
