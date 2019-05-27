---
author: eliotcowley
title: ILearningModelOperatorProviderNative.GetRegistry メソッド
description: カスタム演算子の定義を含む IMLOperatorRegistry オブジェクトを取得します。
ms.author: elcowle
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、GetRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelOperatorProviderNative.GetRegistry
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 9207ae651cc7f8985b3c81f3971834c2c6b629ce
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180124"
---
# <a name="ilearningmodeloperatorprovidernativegetregistry-method"></a>ILearningModelOperatorProviderNative.GetRegistry メソッド

取得、 [IMLOperatorRegistry](../custom-operators/IMLOperatorRegistry.md)カスタム演算子の定義を含むオブジェクト。

```cpp
void GetRegistry(
    IMLOperatorRegistry** ppOperatorRegistry);
```

## <a name="parameters"></a>パラメーター

| 名前 | 種類 | 説明 |
|------|------|-------------|
| ppOperatorRegistry | [IMLOperatorRegistry](../custom-operators/IMLOperatorRegistry.md)** | **IMLOperatorRegistry**カスタム演算子の定義を含むオブジェクト。 |

## <a name="returns"></a>戻り値

**void**このメソッドが値を返しません。

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
