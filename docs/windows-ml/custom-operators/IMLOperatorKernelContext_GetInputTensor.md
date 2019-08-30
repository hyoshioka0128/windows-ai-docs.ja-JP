---
title: Imloperatorカーネルコンテキスト。 Getinputのメソッド
description: 指定したインデックス位置にある演算子によって入力された入力を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、GetInputTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetInputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 8d35408495d4ee08ae42d11d77103bf64fb2bb3f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157301"
---
# <a name="imloperatorkernelcontextgetinputtensor-method"></a>Imloperatorカーネルコンテキスト。 Getinputのメソッド

指定したインデックス位置にある演算子によって入力された入力を取得します。 これにより、存在しない省略可能な入力に対して、このオプションが**nullptr**に設定されます。 指定したインデックス位置にある入力が、まだ存在しない場合はエラーを返します。

```cpp
void GetInputTensor(
    uint32_t inputIndex,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
