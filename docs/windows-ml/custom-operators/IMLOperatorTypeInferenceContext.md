---
title: IMLOperatorTypeInferenceContext インターフェイス
description: 型 inferrers の呼び出し中に、演算子の使用法に関する情報を提供します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IMLOperatorTypeInferenceContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTypeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 43eadcd6deb99e3f525788ceb9b5f2598d6da863
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157903"
---
# <a name="imloperatortypeinferencecontext-interface"></a>IMLOperatorTypeInferenceContext インターフェイス

型 inferrers の呼び出し中に、演算子の使用法に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetInputCount](IMLOperatorTypeInferenceContext_GetInputCount.md) | 演算子への入力の数を取得します。 |
| [GetInputEdgeDescription](IMLOperatorTypeInferenceContext_GetInputEdgeDescription.md) | 演算子の指定した入力エッジの説明を取得します。 |
| [GetOutputCount](IMLOperatorTypeInferenceContext_GetOutputCount.md) | 演算子への出力の数を取得します。 |
| [IsInputValid](IMLOperatorTypeInferenceContext_IsInputValid.md) | 演算子への入力が有効な場合は true を返します。 |
| [IsOutputValid](IMLOperatorTypeInferenceContext_IsOutputValid.md) | 演算子への出力が有効な場合は true を返します。 |
| [SetOutputEdgeDescription](IMLOperatorTypeInferenceContext_SetOutputEdgeDescription.md) | 出力エッジの推定される型を設定します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
