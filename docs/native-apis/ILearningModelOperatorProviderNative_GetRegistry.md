---
author: eliotcowley
title: ILearningModelOperatorProviderNative.GetRegistry メソッド
description: カスタム演算子の定義を含む IMLOperatorRegistry オブジェクトを取得します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 7c058cac69137e1a3a622d1b1bcb8833deaa2342
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473969"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../includes/get-help.md)]
