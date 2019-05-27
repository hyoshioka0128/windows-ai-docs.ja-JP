---
author: eliotcowley
title: IMLOperatorAttributes.GetStringAttributeElementLength メソッド
description: 文字列型の属性要素の長さを取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetStringAttributeElementLength
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElementLength
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 31159c558c7740d35642072e33b373a75e50a77b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181134"
---
# <a name="imloperatorattributesgetstringattributeelementlength-method"></a>IMLOperatorAttributes.GetStringAttributeElementLength メソッド

文字列型の属性要素の長さを取得します。 属性の文字列配列である場合は、このメソッドは、指定したインデックス位置にある属性内の各要素のサイズを照会します。 文字列は utf-8 形式です。  サイズには、null 終端文字が含まれています。

```cpp
void GetStringAttributeElementLength(
    _In_z_ const char* name,
    uint32_t elementIndex,
    _Out_ uint32_t* attributeElementByteSize)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
