---
author: eliotcowley
title: IMLOperatorKernel インターフェイス
description: カスタム演算子カーネルによって実装されます。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 37fb0283336c69d920794726284d774e049e1ec6
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474249"
---
# <a name="imloperatorkernel-interface"></a>IMLOperatorKernel インターフェイス

カスタム演算子カーネルによって実装されます。 使用してカスタム演算子のカーネルを登録するときに、このインターフェイスのインスタンスを作成するファクトリが指定された[IMLOperatorRegistry::RegisterOperatorKernel](IMLOperatorRegistry_RegisterOperatorKernel.md)します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [計算](IMLOperatorKernel_Compute.md) | カーネルの出力を計算します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
