---
author: eliotcowley
title: IMLOperatorTypeInferenceContext インターフェイス
description: 型 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 5b351018b5e4506017ead09c1553958468aed204
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474059"
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
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
