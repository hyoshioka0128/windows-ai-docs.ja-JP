---
author: eliotcowley
title: IMLOperatorRegistry インターフェイス
description: カスタム演算子のカーネルとスキーマについてのレジストリのインスタンスを表します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorRegistry
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorRegistry
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7c1e9f1a026780bfae4fedfdae5244918f07e9bd
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181734"
---
# <a name="imloperatorregistry-interface"></a>IMLOperatorRegistry インターフェイス

カスタム演算子のカーネルとスキーマについてのレジストリのインスタンスを表します。 インスタンスを返すことによって Windows.AI.MachineLearning Api を使用したカスタム演算子を使用する**IMLOperatorRegistry**を通じて**ILearningModelOperatorProviderNative**します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md) | カスタム演算子のカーネルを登録します。 |
| [RegisterOperatorSetSchema](IMLOperatorRegistry_RegisterOperatorSetSchema.md) | 演算子のセットを構成するカスタム演算子のスキーマのセットを登録します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
