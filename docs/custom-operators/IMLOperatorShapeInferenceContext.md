---
author: eliotcowley
title: IMLOperatorShapeInferenceContext インターフェイス
description: 図形 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorShapeInferenceContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: bf5a479c735d06d4609ad9841559dccaf8d0dd30
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474209"
---
# <a name="imloperatorshapeinferencecontext-interface"></a>IMLOperatorShapeInferenceContext インターフェイス

図形 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetInputCount](IMLOperatorShapeInferenceContext_GetInputCount.md) | オペレーターへの入力の数を取得します。 |
| [GetInputEdgeDescription](IMLOperatorShapeInferenceContext_GetInputEdgeDescription.md) | 演算子の指定した入力のエッジの説明を取得します。 |
| [GetInputTensorDimensionCount](IMLOperatorShapeInferenceContext_GetInputTensorDimensionCount.md) | 演算子の利用したテンソル出力の次元数を取得します。 |
| [GetInputTensorShape](IMLOperatorShapeInferenceContext_GetInputTensorShape.md) | 演算子の入力に利用したテンソルの次元のサイズを取得します。 |
| [GetOutputCount](IMLOperatorShapeInferenceContext_GetOutputCount.md) | 演算子には、出力の数を取得します。 |
| [IsInputValid](IMLOperatorShapeInferenceContext_IsInputValid.md) | オペレーターへの入力が有効な場合に true を返します。 |
| [IsOutputValid](IMLOperatorShapeInferenceContext_IsOutputValid.md) | オペレーターへの出力が有効な場合に true を返します。 |
| [SetOutputTensorShape](IMLOperatorShapeInferenceContext_SetOutputTensorShape.md) | 出力 tensor の推定の形状を設定します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
