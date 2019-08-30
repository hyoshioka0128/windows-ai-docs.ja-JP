---
title: IMLOperatorShapeInferenceContext インターフェイス
description: 図形が呼び出されている間に、演算子の使用法に関する情報を提供します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IMLOperatorShapeInferenceContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorShapeInferenceContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 4d8d9ac610c7285a560e76ac87ae9622afc43f53
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157016"
---
# <a name="imloperatorshapeinferencecontext-interface"></a>IMLOperatorShapeInferenceContext インターフェイス

図形が呼び出されている間に、演算子の使用法に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetInputCount](IMLOperatorShapeInferenceContext_GetInputCount.md) | 演算子への入力の数を取得します。 |
| [GetInputEdgeDescription](IMLOperatorShapeInferenceContext_GetInputEdgeDescription.md) | 演算子の指定した入力エッジの説明を取得します。 |
| [GetInputTensorDimensionCount](IMLOperatorShapeInferenceContext_GetInputTensorDimensionCount.md) | 操作のすべての出力の次元数を取得します。 |
| [GetInputTensorShape](IMLOperatorShapeInferenceContext_GetInputTensorShape.md) | 入力された演算子の大きさのサイズを取得します。 |
| [GetOutputCount](IMLOperatorShapeInferenceContext_GetOutputCount.md) | 演算子への出力の数を取得します。 |
| [IsInputValid](IMLOperatorShapeInferenceContext_IsInputValid.md) | 演算子への入力が有効な場合は true を返します。 |
| [IsOutputValid](IMLOperatorShapeInferenceContext_IsOutputValid.md) | 演算子への出力が有効な場合は true を返します。 |
| [SetOutputTensorShape](IMLOperatorShapeInferenceContext_SetOutputTensorShape.md) | 出力の推論された形状を設定します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
