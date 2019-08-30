---
title: Imloperatorの説明。 Getinputの Sordimensioncount メソッド
description: 入力されたオペレーターの入力の次元数を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Getinputの Sordimensioncount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription.GetInputTensorDimensionCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0a7b95025b95b0779d2fae2aa751a32a47392ec9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157797"
---
# <a name="imloperatortensorshapedescriptiongetinputtensordimensioncount-method"></a>Imloperatorの説明。 Getinputの Sordimensioncount メソッド

入力されたオペレーターの入力の次元数を取得します。 指定したインデックス位置にある入力が、まだ存在しない場合はエラーを返します。

```cpp
void GetInputTensorDimensionCount(
    uint32_t inputIndex,
    _Out_ uint32_t* dimensionCount)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
