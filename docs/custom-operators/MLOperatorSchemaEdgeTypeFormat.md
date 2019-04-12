---
author: eliotcowley
title: MLOperatorSchemaEdgeTypeFormat 列挙型
description: 入力と出力の種類でエッジが説明されている方法を指定します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: afaaa167f1608b55c982e7400f2b032c6e444b20
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474569"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
