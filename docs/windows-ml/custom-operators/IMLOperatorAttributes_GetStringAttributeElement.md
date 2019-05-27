---
author: eliotcowley
title: IMLOperatorAttributes.GetStringAttributeElement メソッド
description: 文字列型の属性要素の値を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetStringAttributeElement
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElement
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1012fdb8dde7e30e65cfea0a1c2874032383c3b4
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181064"
---
# <a name="imloperatorattributesgetstringattributeelement-method"></a>IMLOperatorAttributes.GetStringAttributeElement メソッド

文字列型の属性要素の値を取得します。 属性の文字列配列である場合は、このメソッドは、指定したインデックス位置にある属性内の各要素の値を照会します。 文字列は utf-8 形式です。 サイズには、null 終端文字が含まれています。

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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
