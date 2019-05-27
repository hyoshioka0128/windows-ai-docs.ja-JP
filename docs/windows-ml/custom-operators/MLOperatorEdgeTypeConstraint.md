---
author: eliotcowley
title: MLOperatorEdgeTypeConstraint 構造体
description: カスタム演算子のカーネルとスキーマでサポートされているエッジの種類に関連する制約を指定します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorEdgeTypeConstraint
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorEdgeTypeConstraint
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bb9e1e948ab3ed5373c24e4ec4ceb7724cd9e74c
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181394"
---
# <a name="mloperatoredgetypeconstraint-struct"></a>MLOperatorEdgeTypeConstraint 構造体

カスタム演算子のカーネルとスキーマでサポートされているエッジの種類に関連する制約を指定します。 指定された型のラベルの文字列は、同じ演算子を ONNX 仕様にラベルを入力に対応します。 内で指定されたラベルの入力に対応するカスタム スキーマでは、 [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)オペレーターのスキーマを登録するときにします。

## <a name="fields"></a>フィールド

| 名前 | 種類 | 説明 |
|------|------|-------------|
| allowedTypeCount | **uint32_t** | |
| allowedTypes | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md)* | 制約の使用可能なタイプのセット。 |
| typeLabel | **Char*** | 制約が定義されている型のラベルです。 ONNX 演算子スキーマのように構成されています。 たとえば、"T"とします。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
