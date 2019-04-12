---
author: eliotcowley
title: MLOperatorSetId 構造体
description: 演算子セットの id を指定します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorSetId
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSetId
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 54dc199488fc158315b71e8087b6bd3341d800e2
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473989"
---
# <a name="mloperatorsetid-struct"></a>MLOperatorSetId 構造体

演算子セットの id を指定します。

## <a name="fields"></a>フィールド

| 名前 | 種類 | 説明 |
|------|------|-------------|
| ドメイン (domain) | **const char*** | たとえば、"ai.onnx.ml"や ONNX ドメインに空の文字列演算子のドメイン。 |
| version | **int32_t** | 演算子のドメインのバージョン。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
