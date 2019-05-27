---
author: eliotcowley
title: IMLOperatorTypeInferenceContext インターフェイス
description: 型 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorTypeInferenceContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 7af793410357500436142c987b1d3010a6f9b2e4
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180284"
---
# <a name="imloperatortypeinferencecontext-interface"></a>IMLOperatorTypeInferenceContext インターフェイス

型 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetInputCount](IMLOperatorTypeInferenceContext_GetInputCount.md) | オペレーターへの入力の数を取得します。 |
| [GetInputEdgeDescription](IMLOperatorTypeInferenceContext_GetInputEdgeDescription.md) | 演算子の指定した入力のエッジの説明を取得します。 |
| [GetOutputCount](IMLOperatorTypeInferenceContext_GetOutputCount.md) | 演算子には、出力の数を取得します。 |
| [IsInputValid](IMLOperatorTypeInferenceContext_IsInputValid.md) | オペレーターへの入力が有効な場合に true を返します。 |
| [IsOutputValid](IMLOperatorTypeInferenceContext_IsOutputValid.md) | オペレーターへの出力が有効な場合に true を返します。 |
| [SetOutputEdgeDescription](IMLOperatorTypeInferenceContext_SetOutputEdgeDescription.md) | 出力のエッジの推論された型を設定します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
