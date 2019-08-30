---
title: 'Imloperatorによる説明。 Getoutput: Sorshape メソッド'
description: 操作のすべての出力のサイズを取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Getoutput整理 Sorshape
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorShape
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 5d7672315ef36203bfdd6985526c39057d23760b
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157825"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensorshape-method"></a>Imloperatorによる説明。 Getoutput: Sorshape メソッド

操作のすべての出力のサイズを取得します。 指定されたインデックスの出力が、まだ存在しない場合はエラーを返します。

```cpp
GetOutputTensorShape(
    uint32_t outputIndex,
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
