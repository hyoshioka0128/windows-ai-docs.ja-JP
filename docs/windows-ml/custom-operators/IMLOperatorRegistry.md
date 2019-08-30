---
title: IMLOperatorRegistry インターフェイス
description: カスタム演算子カーネルおよびスキーマのレジストリのインスタンスを表します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IMLOperatorRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: fc24c8e43a76b4258471dfed37c5b528699b69db
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157616"
---
# <a name="imloperatorregistry-interface"></a>IMLOperatorRegistry インターフェイス

カスタム演算子カーネルおよびスキーマのレジストリのインスタンスを表します。 カスタム演算子は、 **ILearningModelOperatorProviderNative**を使用して**Imloperatorregistry**のインスタンスを返すことによって、Windows の AI を使用したとして使用することができます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md) | カスタムの演算子カーネルを登録します。 |
| [RegisterOperatorSetSchema](IMLOperatorRegistry_RegisterOperatorSetSchema.md) | 演算子セットを構成するカスタムの演算子スキーマのセットを登録します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
