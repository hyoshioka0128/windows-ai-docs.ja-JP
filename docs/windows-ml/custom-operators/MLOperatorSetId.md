---
author: eliotcowley
title: MLOperatorSetId 構造体
description: 演算子セットの id を指定します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 6c3af6b616a93b9dbf1bdc8d9d951ca2770a6a46
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181304"
---
# <a name="mloperatorsetid-struct"></a>MLOperatorSetId 構造体

演算子セットの id を指定します。

## <a name="fields"></a>フィールド

| 名前 | 種類 | 説明 |
|------|------|-------------|
| ドメイン (domain) | **const char*** | たとえば、"ai.onnx.ml"や ONNX ドメインに空の文字列演算子のドメイン。 |
| version | **int32_t** | 演算子のドメインのバージョン。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
