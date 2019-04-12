---
author: eliotcowley
title: MLOperatorSchemaDescription 構造体
description: そのスキーマを登録に使用される演算子のカスタム スキーマの説明です。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorSchemaDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 051bbb8aa26ab9c3fd83aa38ab928ff54ce93643
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474609"
---
# <a name="mloperatorschemadescription-struct"></a>MLOperatorSchemaDescription 構造体

そのスキーマを登録に使用される演算子のカスタム スキーマの説明です。

## <a name="fields"></a>フィールド

| 名前 | 種類 | 説明 |
|------|------|-------------|
| attributeCount | **uint32_t** | 指定された属性の数。 |
| 属性 | **const** [MLOperatorAttribute](MLOperatorAttribute.md)* | 演算子の種類によってサポートされる属性のセット。 |
| defaultAttributeCount | **uint32_t** | 指定された既定の属性値の数。 |
| defaultAttributes | **const** [MLOperatorAttributeNameValue](MLOperatorAttributeNameValue.md)* | 属性の既定値。 これらは、属性は、演算子の種類を格納しているモデルで不足しているときに適用されます。 |
| inputCount | **uint32_t** | 演算子の入力の数。 |
| 入力 | **const** [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)* | 演算子の説明を格納する配列の端を入力します。 |
| name | **const char*** | NULL で終わる utf-8 文字列演算子の名前を表します。 |
| operatorSetVersionAtLastChange | **int32_t** | 演算子は、この演算子が導入されたまたは最後に変更されたバージョンを設定します。 |
| outputCount | **uint32_t** | 演算子の出力の数。 |
| 出力 | **const** [MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)* | 演算子の説明を格納する配列のエッジを出力します。 |
| typeConstraintCount | **uint32_t** | 指定された型の制約の数。 |
| typeConstraints | **const** [MLOperatorEdgeTypeConstraint](MLOperatorEdgeTypeConstraint.md)* | 型の制約の配列。 各制約では、入力と 1 つまたは複数の境界の種類にラベル文字列の型に関連付けられている出力を制限します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
