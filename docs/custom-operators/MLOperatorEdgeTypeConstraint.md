---
author: eliotcowley
title: MLOperatorEdgeTypeConstraint 構造体
description: カスタム演算子のカーネルとスキーマでサポートされているエッジの種類に関連する制約を指定します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: ccc3f7abed0be9b5a217c3172b3b02ae35197147
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474359"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
