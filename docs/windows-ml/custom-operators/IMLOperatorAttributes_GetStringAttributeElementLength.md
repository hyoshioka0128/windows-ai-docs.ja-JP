---
title: IMLOperatorAttributes。 GetStringAttributeElementLength メソッド
description: 文字列型の属性要素の長さを取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetStringAttributeElementLength
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorAttributes.GetStringAttributeElementLength
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 66726d80d535837344912fafab561a57b87dee98
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157228"
---
# <a name="imloperatorattributesgetstringattributeelementlength-method"></a>IMLOperatorAttributes。 GetStringAttributeElementLength メソッド

文字列型の属性要素の長さを取得します。 文字列配列の属性の場合、このメソッドは、指定されたインデックス位置にある属性内の個々の要素のサイズを照会します。 文字列は UTF-8 形式です。  このサイズには、null 終端文字が含まれます。

```cpp
void GetStringAttributeElementLength(
    _In_z_ const char* name,
    uint32_t elementIndex,
    _Out_ uint32_t* attributeElementByteSize)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
