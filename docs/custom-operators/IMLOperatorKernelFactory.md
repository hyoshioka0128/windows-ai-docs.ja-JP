---
author: eliotcowley
title: IMLOperatorKernelFactory インターフェイス
description: そのカーネルのインスタンスを作成するカスタム演算子のカーネルの作成者によって実装されます。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorKernelFactory
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 28bae41fe0e3e3e97d3b50451e29219b0cdbebbd
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474459"
---
# <a name="imloperatorkernelfactory-interface"></a>IMLOperatorKernelFactory インターフェイス

そのカーネルのインスタンスを作成するカスタム演算子のカーネルの作成者によって実装されます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateKernel](IMLOperatorKernelFactory_CreateKernel.md) | 指定された、指定されたコンテキスト オブジェクトで説明されているモデル内の演算子の使用状況に関する情報に関連する演算子のカーネルのインスタンスを作成します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
