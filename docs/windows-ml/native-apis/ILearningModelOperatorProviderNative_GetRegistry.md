---
title: ILearningModelOperatorProviderNative メソッド
description: カスタム演算子の定義を含む IMLOperatorRegistry オブジェクトを取得します。
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、GetRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelOperatorProviderNative.GetRegistry
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: b82be2740d5c44ff343ec4c16380626abd0852b3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156528"
---
# <a name="ilearningmodeloperatorprovidernativegetregistry-method"></a>ILearningModelOperatorProviderNative メソッド

カスタム演算子の定義を含む[Imloperatorregistry](../custom-operators/IMLOperatorRegistry.md)オブジェクトを取得します。

```cpp
void GetRegistry(
    IMLOperatorRegistry** ppOperatorRegistry);
```

## <a name="parameters"></a>パラメーター

| 名前 | 型 | 説明 |
|------|------|-------------|
| ppOperatorRegistry | [IMLOperatorRegistry](../custom-operators/IMLOperatorRegistry.md)** | カスタム演算子の定義を含む**Imloperatorregistry**オブジェクト。 |

## <a name="returns"></a>戻り値

**void**このメソッドは値を返しません。

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | windows. ai.... .h |

[!INCLUDE [help](../../includes/get-help.md)]
