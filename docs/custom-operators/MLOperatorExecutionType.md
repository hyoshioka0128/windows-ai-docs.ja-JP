---
author: eliotcowley
title: MLOperatorExecutionType 列挙型
description: カーネルが計算のため、CPU または GPU を使用するかどうかを指定します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorExecutionType
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorExecutionType
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0787dd1e4fa2960395ee363710dc94bed118ca43
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474849"
---
# <a name="mloperatorexecutiontype-enum"></a>MLOperatorExecutionType 列挙型

カーネルが計算のため、CPU または GPU を使用するかどうかを指定します。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| 未定義 | 0 | |
| cpu | 1 | |
| D3D12 | 2 | |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
