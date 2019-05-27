---
author: eliotcowley
title: IMLOperatorTensor.GetData メソッド
description: テンソルのバイトのアドレス指定可能なメモリへのポインターを返します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 52ec28b5929fb9ee6eb987c6210e41ce5634bb62
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181074"
---
# <a name="imloperatortensorgetdata-method"></a>IMLOperatorTensor.GetData メソッド

テンソルのバイトのアドレス指定可能なメモリへのポインターを返します。 可能性がある際に使用される[IMLOperatorTensor::IsDataInterface](IMLOperatorTensor_IsDataInterface.md)を使用して、カーネルが登録されているために、false を返します[MLOperatorExecutionType::Cpu](MLOperatorExecutionType.md)します。 データのサイズは利用したテンソルの図形から派生します。 これは完全に、メモリ内でパックします。

```cpp
void* GetData()
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
