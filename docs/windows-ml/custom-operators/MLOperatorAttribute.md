---
title: MLOperatorAttribute 構造体
description: カスタム演算子の属性の名前とプロパティを指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorAttribute
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorAttribute
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7ddd6fa76b920c4901aae9d2583f6b9d15a17c75
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157945"
---
# <a name="mloperatorattribute-struct"></a>MLOperatorAttribute 構造体

カスタム演算子の属性の名前とプロパティを指定します。 これは、カスタム演算子カーネルとカスタム演算子スキーマを登録するときに使用されます。

## <a name="fields"></a>フィールド

| 名前     | 型                    | 説明 |
|----------|-------------------------|-------------|
| NAME     | **char***                   | NULL で終わる UTF-8 文字列で、関連付けられている演算子の種類の属性の名前を表します。 |
| required | **bool**                    | 関連付けられている演算子の種類を使用しているモデルでは、属性が必須かどうか。 |
| type     | [MLOperatorAttributeType](MLOperatorAttributeType.md) | 関連付けられている演算子の種類の属性の型。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
