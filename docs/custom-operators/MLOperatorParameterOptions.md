---
author: eliotcowley
title: MLOperatorParameterOptions 列挙型
description: 演算子の入力と出力のオプション フラグを指定します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 61e14be6c729c52312ee3d3a47bfd6bc49a58f5b
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474189"
---
# <a name="mloperatorparameteroptions-enum"></a>MLOperatorParameterOptions 列挙型

演算子の入力と出力のオプション フラグを指定します。 これらのオプションは、カスタム演算子のスキーマを定義するときに使用されます。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| 単一 | 0 | 入力または出力の 1 つのインスタンスがあります。 |
| 省略可能 | 1 | 入力または出力を省略できます。 |
| 可変個引数 | 2 | 演算子のインスタンスの数は、変数です。 可変個引数パラメーターは、最後に一連の入力または出力の間で指定する必要があります。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
