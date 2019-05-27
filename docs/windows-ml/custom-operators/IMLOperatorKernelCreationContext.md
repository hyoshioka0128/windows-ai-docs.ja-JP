---
author: eliotcowley
title: IMLOperatorKernelCreationContext インターフェイス
description: カーネルの作成中には、演算子の使用状況に関する情報を提供します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorKernelCreationContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelCreationContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: edb6199be8fd9233612e3b18a9047d955ab332b8
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181524"
---
# <a name="imloperatorkernelcreationcontext-interface"></a>IMLOperatorKernelCreationContext インターフェイス

カーネルの作成中には、演算子の使用状況に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetExecutionInterface](IMLOperatorKernelCreationContext_GetExecutionInterface.md) | カーネルの種類に基づいて、サポートされているインターフェイスが異なるオブジェクトを返します。 |
| [GetInputCount](IMLOperatorKernelCreationContext_GetInputCount.md) | オペレーターへの入力の数を取得します。 |
| [GetInputEdgeDescription](IMLOperatorKernelCreationContext_GetInputEdgeDescription.md) | 演算子の指定した入力のエッジの説明を取得します。 |
| [GetOutputCount](IMLOperatorKernelCreationContext_GetOutputCount.md) | 演算子には、出力の数を取得します。 |
| [GetOutputEdgeDescription](IMLOperatorKernelCreationContext_GetOutputEdgeDescription.md) | 演算子の指定した出力のエッジの説明を取得します。 |
| [GetTensorShapeDescription](IMLOperatorKernelCreationContext_GetTensorShapeDescription.md) | 演算子の端に接続されている入力と出力の図形の説明を取得します。 |
| [HasTensorShapeDescription](IMLOperatorKernelCreationContext_HasTensorShapeDescription.md) | 演算子の端に入力と出力の図形の説明が接続されている場合は true を返しますを使用して照会することがあります**GetTensorShapeDescription**します。 |
| [IsInputValid](IMLOperatorKernelCreationContext_IsInputValid.md) | オペレーターへの入力が有効な場合に true を返します。 常に true を返します省略可能な入力を除く。 |
| [IsOutputValid](IMLOperatorKernelCreationContext_IsOutputValid.md) | オペレーターへの出力が有効な場合に true を返します。 常に true を返します省略可能な出力を除く。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
