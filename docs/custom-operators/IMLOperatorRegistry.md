---
author: eliotcowley
title: IMLOperatorRegistry インターフェイス
description: カスタム演算子のカーネルとスキーマについてのレジストリのインスタンスを表します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: e3e2edd778a63a06760c6fd46b096e88db4f5cdb
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474079"
---
# <a name="imloperatorregistry-interface"></a>IMLOperatorRegistry インターフェイス

カスタム演算子のカーネルとスキーマについてのレジストリのインスタンスを表します。 インスタンスを返すことによって Windows.AI.MachineLearning Api を使用したカスタム演算子を使用する**IMLOperatorRegistry**を通じて**ILearningModelOperatorProviderNative**します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md) | カスタム演算子のカーネルを登録します。 |
| [RegisterOperatorSetSchema](IMLOperatorRegistry_RegisterOperatorSetSchema.md) | 演算子のセットを構成するカスタム演算子のスキーマのセットを登録します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
