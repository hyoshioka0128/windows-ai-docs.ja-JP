---
title: Imloperatortenantsorshape の説明。 Getinputを Sorshape メソッド
description: 入力された演算子の大きさのサイズを取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Getinput整理 Sorshape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 2fb2e3c059e458457f3c77f04e9c3203bd332932
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157240"
---
# <a name="imloperatortensorshapedescriptiongetinputtensorshape-method"></a>Imloperatortenantsorshape の説明。 Getinputを Sorshape メソッド

入力された演算子の大きさのサイズを取得します。 指定したインデックス位置にある入力が、まだ存在しない場合はエラーを返します。

```cpp
void GetInputTensorShape(
    uint32_t inputIndex,
    uint32_t dimensionCount,
    _Out_writes_(dimensionCount) uint32_t* dimensions)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
