---
author: eliotcowley
title: IMLOperatorAttributes.GetStringAttributeElementLength メソッド
description: 文字列型の属性要素の長さを取得します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 633e97ce0533b514a6540b848fef397b87cbc008
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474539"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
