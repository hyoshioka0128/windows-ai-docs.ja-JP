---
author: eliotcowley
title: IMLOperatorAttributes.GetAttributeElementCount メソッド
description: 属性内の要素数を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetAttributeElementCount
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttributeElementCount
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 06ef30b8d2e9c21a081a97311471c62ab0211b25
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180654"
---
# <a name="imloperatorattributesgetattributeelementcount-method"></a>IMLOperatorAttributes.GetAttributeElementCount メソッド

属性内の要素数を取得します。 属性が存在するかを判断し、配列型の属性内の要素の数を決定することができる指定します。

```cpp
void GetAttributeElementCount(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    _Out_ uint32_t* elementCount)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
