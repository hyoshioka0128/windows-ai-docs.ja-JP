---
title: Imloperatorの説明。 Getoutputの Sordimensioncount メソッド
description: 操作のすべての出力の次元数を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetOutputTensorDimensionCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetOutputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c1010e2f0abbb92b36399d5c1938673b4a002c53
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157814"
---
# <a name="imloperatortensorshapedescriptiongetoutputtensordimensioncount-method"></a>Imloperatorの説明。 Getoutputの Sordimensioncount メソッド

操作のすべての出力の次元数を取得します。 指定されたインデックスの出力が、まだ存在しない場合はエラーを返します。

```cpp
GetOutputTensorDimensionCount(
    uint32_t outputIndex,
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
