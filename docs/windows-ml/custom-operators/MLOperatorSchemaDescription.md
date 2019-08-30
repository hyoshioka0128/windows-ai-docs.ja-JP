---
title: MLOperatorSchemaDescription 構造体
description: スキーマの登録に使用されるカスタムオペレータースキーマの説明です。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorSchemaDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 84f5cd88f20de2df8fce2bfca34d082352ab6536
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157687"
---
# <a name="mloperatorschemadescription-struct"></a>MLOperatorSchemaDescription 構造体

スキーマの登録に使用されるカスタムオペレータースキーマの説明です。

## <a name="fields"></a>フィールド

| 名前 | 型 | 説明 |
|------|------|-------------|
| 属性の Ecount | **uint32_t** | 指定された属性の数。 |
| 属性 | **const**[Mloperatorattribute](MLOperatorAttribute.md)* | 演算子型によってサポートされる属性のセット。 |
| Default属性の Ecount | **uint32_t** | 指定された既定の属性値の数。 |
| defaultAttributes | **const**[MLOperatorAttributeNameValue](MLOperatorAttributeNameValue.md)* | 属性の既定値。 これらは、演算子の型を含むモデルで属性が指定されていない場合に適用されます。 |
| inputCount | **uint32_t** | 演算子の入力の数。 |
| 入力 | **const**[MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)* | 演算子の入力エッジの説明を格納している配列。 |
| NAME | **const char*** | NULL で終わる、演算子の名前を表す UTF-8 文字列。 |
| オペレーター Setversionatlastchange | **int32_t** | この演算子が導入された、または最後に変更された演算子セットのバージョン。 |
| outputCount | **uint32_t** | 演算子の出力の数。 |
| 出力 | **const**[MLOperatorSchemaEdgeDescription](MLOperatorSchemaEdgeDescription.md)* | 演算子の出力エッジの説明を格納している配列。 |
| typeConstraintCount | **uint32_t** | 指定された型制約の数。 |
| typeConstraints | **const**[MLOperatorEdgeTypeConstraint](MLOperatorEdgeTypeConstraint.md)* | 型制約の配列。 各制約では、型ラベル文字列に関連付けられている入力と出力を1つ以上のエッジ型に制限します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
