---
title: MLOperatorKernelDescription 構造体
description: スキーマを登録するために使用されるカスタムオペレーターカーネルの説明。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Mloperatorカーネルの説明
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorKernelDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 2f16c86805d162ceb14d9df629f94e1516d3b5d3
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157699"
---
# <a name="mloperatorkerneldescription-struct"></a>MLOperatorKernelDescription 構造体

スキーマを登録するために使用されるカスタムオペレーターカーネルの説明。

## <a name="fields"></a>フィールド

| 名前 | 型 | 説明 |
|------|------|-------------|
| Default属性の Ecount | **uint32_t** | 指定された既定の属性値の数。 |
| defaultAttributes | **const**[MLOperatorAttributeNameValue](MLOperatorAttributeNameValue.md)* | 属性の既定値。 これらは、演算子の型を含むモデルで属性が指定されていない場合に適用されます。 |
| domain | **const char*** | オペレーターのドメインの名前を表す、NULL で終わる UTF-8 文字列。 |
| executionOptions | **uint32_t** | 追加オプション用に予約されています。 0 を指定する必要があります。 |
| executionType | [MLOperatorExecutionType](MLOperatorExecutionType.md) | カーネルが計算に CPU と GPU のどちらを使用するかを指定します。 |
| minimumOperatorSetVersion | **int32_t** | このカーネルが有効な演算子セットの最小バージョン。 最大バージョンは、同じドメインの後続のバージョンに対するオペレーターセットスキーマの登録に基づいて推定されます。 |
| NAME | **const char*** | NULL で終わる、演算子の名前を表す UTF-8 文字列。 |
| options | [MLOperatorKernelOptions](MLOperatorKernelOptions.md) | カーネルのオプション。すべての実行プロバイダーの種類に適用されます。 |
| typeConstraintCount | **uint32_t** | 指定された型制約の数。 |
| typeConstraints | **const**[MLOperatorEdgeTypeConstraint](MLOperatorEdgeTypeConstraint.md)* | 型制約の配列。 各制約では、型ラベル文字列に関連付けられている入力と出力を1つ以上のエッジ型に制限します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
