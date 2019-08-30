---
title: MLOperatorParameterOptions 列挙型
description: 入力および出力の演算子のエッジのオプションフラグを指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10, windows machine learning, WinML, カスタム演算子, MLOperatorParameterOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorParameterOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 15bfeb20412bc1e9ee3db032fe26fb1d86ab2dc5
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157702"
---
# <a name="mloperatorparameteroptions-enum"></a>MLOperatorParameterOptions 列挙型

入力および出力の演算子のエッジのオプションフラグを指定します。 これらのオプションは、カスタムの演算子スキーマを定義するときに使用します。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| 単一 | 0 | 入力または出力のインスタンスは1つだけです。 |
| 省略可 | 1 | 入力または出力を省略できます。 |
| 可変個引数 | 2 | 演算子のインスタンスの数は可変です。 可変個引数パラメーターは、一連の入力または出力の最後にある必要があります。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
