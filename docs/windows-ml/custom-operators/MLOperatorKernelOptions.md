---
author: eliotcowley
title: MLOperatorKernelOptions 列挙型
description: カスタム演算子のカーネルを登録するときに使用するオプションを指定します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorKernelOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorKernelOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 26861c7d8b1d154aa9ae9f8c5fc12e7e06f6ad7e
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182034"
---
# <a name="mloperatorkerneloptions-enum"></a>MLOperatorKernelOptions 列挙型

カスタム演算子のカーネルを登録するときに使用するオプションを指定します。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| なし | 0 | |
| AllowDynamicInputShapes | 1 | 入力 tensors の図形が演算子のカーネル インスタンスの呼び出しの間で異なる場合にできるかどうかを指定します。 設定されていない場合、カーネルのインスタンスが入力 tensor 図形を作成中に、クエリを更新した後、これらの図形に依存する初期化作業を前面給紙可能性があります。 この設定により、図形は、推論操作間を動的に変わるし、カーネルの実装は、これを効率的に処理する場合、パフォーマンスが向上します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
