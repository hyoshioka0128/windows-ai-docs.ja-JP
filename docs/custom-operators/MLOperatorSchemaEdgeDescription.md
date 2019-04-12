---
author: eliotcowley
title: MLOperatorSchemaEdgeDescription 構造体
description: 演算子の入力または出力エッジに関する情報を指定します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorSchemaEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 28bcd8fff05f99cfaa007ea57b9b17674ba2c3f3
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474409"
---
# <a name="mloperatorschemaedgedescription-struct"></a>MLOperatorSchemaEdgeDescription 構造体

演算子の入力または出力エッジに関する情報を指定します。 これは、カスタム演算子のスキーマを定義する際に使用されます。

## <a name="fields"></a>フィールド

| 名前 | 種類 | 説明 |
|------|------|-------------|
| edgeDescription | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md) | 構造の記述型サポート。 これは、使用時に**typeFormat**は**MLOperatorSchemaEdgeTypeFormat::EdgeDescription**します。 |
| オプション | [MLOperatorParameterOptions](MLOperatorParameterOptions.md) | 省略可能かどうかなど、パラメーターまたは可変個引数のオプションです。 |
| 予約されています | **void*** | |
| typeFormat | [MLOperatorSchemaEdgeTypeFormat](MLOperatorSchemaEdgeTypeFormat.md) | 型の制約と型のマッピングを定義する方法。 |
| typeLabel | **Char*** | ONNX 演算子スキーマのように構築された型のラベルの文字列。 たとえば、"T"とします。 これは、使用時に**typeFormat**は**MLOperatorSchemaEdgeTypeFormat::Label**します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
