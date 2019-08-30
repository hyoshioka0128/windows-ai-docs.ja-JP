---
title: IMLOperatorAttributes メソッド
description: 数値型の属性要素の値を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 69c886c7b8b837cff01d12d369debf924a3d9160
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157075"
---
# <a name="imloperatorattributesgetattribute-method"></a>IMLOperatorAttributes メソッド

数値型の属性要素の値を取得します。 配列型の属性の場合、このメソッドは、指定されたインデックス位置にある属性内の個々の要素を照会します。

```cpp
void GetAttribute(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    uint32_t elementCount,
    size_t elementByteSize,
    _Out_writes_bytes_(elementCount * elementByteSize) void* value)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
