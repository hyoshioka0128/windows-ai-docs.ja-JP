---
author: eliotcowley
title: IMLOperatorAttributes.GetAttribute メソッド
description: 数値型の属性要素の値を取得します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 6d048cf3f4a38ba066940f73060bc6238aed87a4
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474599"
---
# <a name="imloperatorattributesgetattribute-method"></a>IMLOperatorAttributes.GetAttribute メソッド

数値型の属性要素の値を取得します。 配列型の属性の場合は、このメソッドは、指定したインデックス位置にある属性内の各要素を照会します。

```cpp
void GetAttribute(
    _In_z_ const char* name,
    MLOperatorAttributeType type,
    uint32_t elementCount,
    size_t elementByteSize,
    _Out_writes_bytes_(elementCount * elementByteSize) void* value)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
