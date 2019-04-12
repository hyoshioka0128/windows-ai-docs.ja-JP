---
author: eliotcowley
title: IMLOperatorKernelContext.GetInputTensor メソッド
description: 指定したインデックス位置にある演算子の入力 tensor を取得します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 288e2f13f1eaf92a435047fd48c739f017b1d877
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474349"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
