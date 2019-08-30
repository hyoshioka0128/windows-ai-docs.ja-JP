---
title: IMLOperatorAttributes. GetStringAttributeElement メソッド
description: 文字列型の属性要素の値を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetStringAttributeElement
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElement
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 971312a00bb7d8995cf1c1fc1a19dafb20143854
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157105"
---
# <a name="imloperatorattributesgetstringattributeelement-method"></a>IMLOperatorAttributes. GetStringAttributeElement メソッド

文字列型の属性要素の値を取得します。 文字列配列の属性の場合、このメソッドは、指定されたインデックス位置にある属性内の個々の要素の値を照会します。 文字列は UTF-8 形式です。 このサイズには、null 終端文字が含まれます。

```cpp
void GetStringAttributeElement(
    _In_z_ const char* name,
    uint32_t elementIndex,
    uint32_t attributeElementByteSize,
    _Out_writes_(uint32_t) char* attributeElement)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
