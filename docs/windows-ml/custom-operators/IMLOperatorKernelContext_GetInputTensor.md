---
author: eliotcowley
title: IMLOperatorKernelContext.GetInputTensor メソッド
description: 指定したインデックス位置にある演算子の入力 tensor を取得します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetInputTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetInputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b848390fb31231bd30bbe3beaa3020d97f729b68
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180784"
---
# <a name="imloperatorkernelcontextgetinputtensor-method"></a>IMLOperatorKernelContext.GetInputTensor メソッド

指定したインデックス位置にある演算子の入力 tensor を取得します。 これにより、利用したテンソルに設定**nullptr**存在しない入力が省略可能。 指定したインデックス位置にある入力を利用したテンソルでない場合は、エラーを返します。

```cpp
void GetInputTensor(
    uint32_t inputIndex, 
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
