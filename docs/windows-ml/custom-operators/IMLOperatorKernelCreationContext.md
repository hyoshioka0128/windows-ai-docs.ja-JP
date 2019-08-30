---
title: Imloperatorカーネルのコンテキストインターフェイス
description: カーネルの作成中にオペレーターの使用状況に関する情報を提供します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Imloperatorカーネルのコンテキスト
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: df366d878a9ff05b3802e1791cb5476ae50225af
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156840"
---
# <a name="imloperatorkernelcreationcontext-interface"></a>Imloperatorカーネルのコンテキストインターフェイス

カーネルの作成中にオペレーターの使用状況に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetExecutionInterface](IMLOperatorKernelCreationContext_GetExecutionInterface.md) | カーネルの種類によってサポートされるインターフェイスが異なるオブジェクトを返します。 |
| [GetInputCount](IMLOperatorKernelCreationContext_GetInputCount.md) | 演算子への入力の数を取得します。 |
| [GetInputEdgeDescription](IMLOperatorKernelCreationContext_GetInputEdgeDescription.md) | 演算子の指定した入力エッジの説明を取得します。 |
| [GetOutputCount](IMLOperatorKernelCreationContext_GetOutputCount.md) | 演算子への出力の数を取得します。 |
| [GetOutputEdgeDescription](IMLOperatorKernelCreationContext_GetOutputEdgeDescription.md) | 演算子の指定した出力エッジの説明を取得します。 |
| [GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md) | 演算子の端に接続されている入力図形と出力図形の説明を取得します。 |
| [HasTensorShapeDescription](IMLOperatorKernelCreationContext_HasTensorShapeDescription.md) | 演算子のエッジに接続されている入力図形および出力図形の説明が、 **getthe Gettenantsorshapes description**を使用して照会される場合は true を返します。 |
| [IsInputValid](IMLOperatorKernelCreationContext_IsInputValid.md) | 演算子への入力が有効な場合は true を返します。 これは、省略可能な入力を除き、常に true を返します。 |
| [IsOutputValid](IMLOperatorKernelCreationContext_IsOutputValid.md) | 演算子への出力が有効な場合は true を返します。 これは、省略可能な出力を除き、常に true を返します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
