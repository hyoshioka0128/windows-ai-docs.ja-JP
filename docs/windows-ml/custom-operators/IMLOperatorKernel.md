---
author: eliotcowley
title: IMLOperatorKernel インターフェイス
description: カスタム演算子カーネルによって実装されます。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 20799a9544cb880da5f63b37ba53b054dbd5afae
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180704"
---
# <a name="imloperatorkernel-interface"></a>IMLOperatorKernel インターフェイス

カスタム演算子カーネルによって実装されます。 使用してカスタム演算子のカーネルを登録するときに、このインターフェイスのインスタンスを作成するファクトリが指定された[IMLOperatorRegistry::RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md)します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [コンピューティング](IMLOperatorKernel_Compute.md) | カーネルの出力を計算します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
