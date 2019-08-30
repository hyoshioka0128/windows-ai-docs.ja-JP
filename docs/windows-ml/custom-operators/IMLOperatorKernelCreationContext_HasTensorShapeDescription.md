---
title: ImloperatorHasTensorShapeDescription メソッド
description: 演算子のエッジに接続されている入力図形および出力図形の説明が、 **getthe Gettenantsorshapes description**を使用して照会される場合は true を返します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、HasTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext.HasTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bee295251bd04c0d7b6bda6bdd6d1f1e835f4543
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157533"
---
# <a name="imloperatorkernelcreationcontexthastensorshapedescription-method"></a>ImloperatorHasTensorShapeDescription メソッド

演算子のエッジに接続されている入力図形と出力図形の説明が、 [Imloperatorの](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md)記述を使用してクエリされる可能性がある場合に true を返します。 これは、 [MLOperatorKernelOptions:: AllowDynamicInputShapes](MLOperatorKernelOptions.md)フラグを使用して演算子が登録されていない限り、true を返します。

```cpp
bool HasTensorShapeDescription()
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
