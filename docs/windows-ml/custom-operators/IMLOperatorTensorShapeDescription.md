---
author: eliotcowley
title: IMLOperatorTensorShapeDescription インターフェイス
description: 演算子の入力と出力の tensor 図形のセットを表します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorTensorShapeDescription
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensorShapeDescription
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 1ec7c6f185b65b6920887570ce3758d1f21a3d0b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181664"
---
# <a name="imloperatortensorshapedescription-interface"></a>IMLOperatorTensorShapeDescription インターフェイス

演算子の入力と出力の tensor 図形のセットを表します。 このインターフェイスは、カーネルの作成に登録されているファクトリ オブジェクトによって呼び出されます。 使用して対応するカーネルが登録されていない限り、これらのファクトリ オブジェクトで使用、 [MLOperatorKernelOptions::AllowDynamicInputShapes](MLOperatorKernelOptions.md)フラグ。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetInputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetInputTensorDimensionCount.md) | 演算子の利用したテンソル入力の次元数を取得します。 |
| [GetInputTensorShape](IMLOperatorTensorShapeDescription_GetInputTensorShape.md) | 演算子の入力に利用したテンソルの次元のサイズを取得します。 |
| [GetOutputTensorDimensionCount](IMLOperatorTensorShapeDescription_GetOutputTensorDimensionCount.md) | 演算子の利用したテンソル出力の次元数を取得します。 |
| [GetOutputTensorShape](IMLOperatorTensorShapeDescription_GetOutputTensorShape.md) | 演算子の利用したテンソル出力の次元のサイズを取得します。 |
| [HasOutputShapeDescription](IMLOperatorTensorShapeDescription_HasOutputShapeDescription.md) | 使用して、出力の図形をクエリすることがある場合は true を返します**GetOutputTensorDimensionCount**と**GetOutputTensorShape**します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
