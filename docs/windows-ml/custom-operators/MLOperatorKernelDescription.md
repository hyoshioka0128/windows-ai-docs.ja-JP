---
author: eliotcowley
title: MLOperatorKernelDescription 構造体
description: そのスキーマを登録するために使用するカスタム演算子カーネルの説明です。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を MLOperatorKernelDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorKernelDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 69497372f547da6e26a003185f9eba84a19de1be
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181374"
---
# <a name="mloperatorkerneldescription-struct"></a>MLOperatorKernelDescription 構造体

そのスキーマを登録するために使用するカスタム演算子カーネルの説明です。

## <a name="fields"></a>フィールド

| 名前 | 種類 | 説明 |
|------|------|-------------|
| defaultAttributeCount | **uint32_t** | 指定された既定の属性値の数。 |
| defaultAttributes | **const** [MLOperatorAttributeNameValue](MLOperatorAttributeNameValue.md)* | 属性の既定値。 これらは、属性は、演算子の種類を格納しているモデルで不足しているときに適用されます。 |
| ドメイン (domain) | **const char*** | NULL で終わる utf-8 文字列演算子のドメインの名前を表します。 |
| executionOptions | **uint32_t** | 追加のオプションの予約されています。 0 を指定する必要があります。 |
| executionType | [MLOperatorExecutionType](MLOperatorExecutionType.md) | カーネルが計算のため、CPU または GPU を使用するかどうかを指定します。 |
| minimumOperatorSetVersion | **int32_t** | 演算子の最小バージョンの設定のこのカーネルは無効です。 最大バージョンは、同じドメインの後続バージョン演算子セットのスキーマの登録に基づく推測されます。 |
| name | **const char*** | NULL で終わる utf-8 文字列演算子の名前を表します。 |
| オプション | [MLOperatorKernelOptions](MLOperatorKernelOptions.md) | 実行のすべてのプロバイダー型に適用されるカーネルのオプションです。 |
| typeConstraintCount | **uint32_t** | 指定された型の制約の数。 |
| typeConstraints | **const** [MLOperatorEdgeTypeConstraint](MLOperatorEdgeTypeConstraint.md)* | 型の制約の配列。 各制約では、入力と 1 つまたは複数の境界の種類にラベル文字列の型に関連付けられている出力を制限します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
