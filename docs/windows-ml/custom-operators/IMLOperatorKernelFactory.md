---
author: eliotcowley
title: IMLOperatorKernelFactory インターフェイス
description: そのカーネルのインスタンスを作成するカスタム演算子のカーネルの作成者によって実装されます。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 7c0883e426d5c85f013827e3d48193ab14415426
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180454"
---
# <a name="imloperatorkernelfactory-interface"></a>IMLOperatorKernelFactory インターフェイス

そのカーネルのインスタンスを作成するカスタム演算子のカーネルの作成者によって実装されます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateKernel](IMLOperatorKernelFactory_CreateKernel.md) | 指定された、指定されたコンテキスト オブジェクトで説明されているモデル内の演算子の使用状況に関する情報に関連する演算子のカーネルのインスタンスを作成します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
