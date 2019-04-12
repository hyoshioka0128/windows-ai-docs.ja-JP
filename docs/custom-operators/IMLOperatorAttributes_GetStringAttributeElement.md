---
author: eliotcowley
title: IMLOperatorAttributes.GetStringAttributeElement メソッド
description: 文字列型の属性要素の値を取得します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 0dce6fabffcbe9bb6176ba86a4632facd9c9635b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474769"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
