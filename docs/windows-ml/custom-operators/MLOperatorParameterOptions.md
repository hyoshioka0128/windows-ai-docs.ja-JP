---
author: eliotcowley
title: MLOperatorParameterOptions 列挙型
description: 演算子の入力と出力のオプション フラグを指定します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorParameterOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorParameterOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: e348d8a41d1c940f396474844db296f8e1ad323b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181354"
---
# <a name="mloperatorparameteroptions-enum"></a>MLOperatorParameterOptions 列挙型

演算子の入力と出力のオプション フラグを指定します。 これらのオプションは、カスタム演算子のスキーマを定義するときに使用されます。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| 単一 | 0 | 入力または出力の 1 つのインスタンスがあります。 |
| 省略可能 | 1 | 入力または出力を省略できます。 |
| 可変個引数 | 2 | 演算子のインスタンスの数は、変数です。 可変個引数パラメーターは、最後に一連の入力または出力の間で指定する必要があります。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
