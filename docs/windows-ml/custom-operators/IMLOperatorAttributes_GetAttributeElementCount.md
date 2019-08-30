---
title: IMLOperatorAttributes. GetAttributeElementCount メソッド
description: 属性内の要素の数を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetAttributeElementCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttributeElementCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 49495e21eb79e04dae926bf03e67be3de0e396e3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157046"
---
# <a name="imloperatorattributesgetattributeelementcount-method"></a>IMLOperatorAttributes. GetAttributeElementCount メソッド

属性内の要素の数を取得します。 これは、属性が存在するかどうかを判断し、配列型の属性内の要素の数を確認するために使用できます。

```cpp
void GetAttributeElementCount(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    _Out_ uint32_t* elementCount)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
