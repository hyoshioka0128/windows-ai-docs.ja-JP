---
title: MLOperatorSchemaEdgeDescription 構造体
description: 演算子の入力または出力エッジに関する情報を指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorSchemaEdgeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorSchemaEdgeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 49f0e77e0e97a6f2e4cc6454eed261b1961f89a6
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156766"
---
# <a name="mloperatorschemaedgedescription-struct"></a>MLOperatorSchemaEdgeDescription 構造体

演算子の入力または出力エッジに関する情報を指定します。 これは、カスタムの演算子スキーマを定義するときに使用されます。

## <a name="fields"></a>フィールド

| 名前 | 型 | 説明 |
|------|------|-------------|
| edgeDescription | [MLOperatorEdgeDescription](MLOperatorEdgeDescription.md) | 型のサポートを記述する構造体。 **Typeformat**が**MLOperatorSchemaEdgeTypeFormat:: EdgeDescription**の場合に使用されます。 |
| options | [MLOperatorParameterOptions](MLOperatorParameterOptions.md) | パラメーターのオプション (オプションまたは可変個引数かどうかなど)。 |
| 確保 | **void*** | |
| typeFormat | [MLOperatorSchemaEdgeTypeFormat](MLOperatorSchemaEdgeTypeFormat.md) | 型の制約と型のマッピングを定義する方法。 |
| typeLabel | **char*** | ONNX operator スキーマとして構築された型ラベル文字列。 たとえば、"T" のようになります。 **Typeformat**が**MLOperatorSchemaEdgeTypeFormat:: Label**の場合に使用されます。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
