---
title: Imloperatorカーネルの説明メソッド。
description: 演算子の端に接続されている入力図形と出力図形の説明を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Gettenantsormachines の説明
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.GetTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fc2b411d69da09e9b136b647e6ab7f27b7b4620c
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157337"
---
# <a name="imloperatorkernelcreationcontextgettensorshapedescription-method"></a>Imloperatorカーネルの説明メソッド。

演算子の端に接続されている入力図形と出力図形の説明を取得します。

```cpp
void GetTensorShapeDescription(
    _COM_Outptr_ IMLOperatorTensorShapeDescription** shapeDescription)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
