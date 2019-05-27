---
author: eliotcowley
title: MLOperatorSchemaEdgeDescription 構造体
description: 演算子の入力または出力エッジに関する情報を指定します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 82566b25ae7d3f446b4e53a4d0c3d619f21732ca
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181334"
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

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
