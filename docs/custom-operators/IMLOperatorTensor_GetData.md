---
author: eliotcowley
title: IMLOperatorTensor.GetData メソッド
description: テンソルのバイトのアドレス指定可能なメモリへのポインターを返します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetData
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor.GetData
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f3a5e926901c315124dd235b18bc3e6aa5072b6e
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474299"
---
# <a name="imloperatortensorgetdata-method"></a>IMLOperatorTensor.GetData メソッド

テンソルのバイトのアドレス指定可能なメモリへのポインターを返します。 可能性がある際に使用される[IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md)を使用して、カーネルが登録されているために、false を返します[MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md)します。 データのサイズは利用したテンソルの図形から派生します。 これは完全に、メモリ内でパックします。

```cpp
void* GetData()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
