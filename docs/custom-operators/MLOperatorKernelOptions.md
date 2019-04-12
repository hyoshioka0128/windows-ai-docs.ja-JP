---
author: eliotcowley
title: MLOperatorKernelOptions 列挙型
description: カスタム演算子のカーネルを登録するときに使用するオプションを指定します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 078694e26e255bf2e4d2472e8fe3cc8e41f92534
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474709"
---
# <a name="mloperatorkerneloptions-enum"></a>MLOperatorKernelOptions 列挙型

カスタム演算子のカーネルを登録するときに使用するオプションを指定します。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| なし | 0 | |
| AllowDynamicInputShapes | 1 | 入力 tensors の図形が演算子のカーネル インスタンスの呼び出しの間で異なる場合にできるかどうかを指定します。 設定されていない場合、カーネルのインスタンスが入力 tensor 図形を作成中に、クエリを更新した後、これらの図形に依存する初期化作業を前面給紙可能性があります。 この設定により、図形は、推論操作間を動的に変わるし、カーネルの実装は、これを効率的に処理する場合、パフォーマンスが向上します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
