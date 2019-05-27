---
author: eliotcowley
title: MLOperatorSchemaEdgeTypeFormat 列挙型
description: 入力と出力の種類でエッジが説明されている方法を指定します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorSchemaEdgeTypeFormat
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeTypeFormat
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 736ce313193b722ac0d42b2c35c3aae0c45abc33
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181324"
---
# <a name="mloperatorschemaedgetypeformat-enum"></a>MLOperatorSchemaEdgeTypeFormat 列挙型

入力と出力の種類でエッジが説明されている方法を指定します。 これは内で使用[MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)カスタム演算子のスキーマを定義するときにします。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| edgeDescription | 0 | 使用して、型が定義されて[MLOperatorEdgeDescription](MLOperatorEdgeDescription.md)します。 |
| Label | 1 | 種類は、ONNX 演算子スキーマのように構築された型の文字列によって定義されます。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
