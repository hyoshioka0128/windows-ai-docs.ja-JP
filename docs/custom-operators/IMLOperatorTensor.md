---
author: eliotcowley
title: IMLOperatorTensor インターフェイス
description: カスタム演算子のカーネルの計算中に使用される利用したテンソルの表現。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: e8058a31a86ac71724b1bee887049553bd418134
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474199"
---
# <a name="imloperatortensor-interface"></a>IMLOperatorTensor インターフェイス

カスタム演算子のカーネルの計算中に使用される利用したテンソルの表現。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetData](IMLOperatorTensor_GetData.md) | テンソルのバイトのアドレス指定可能なメモリへのポインターを返します。 |
| [GetDataInterface](IMLOperatorTensor_GetDataInterface.md) | テンソルのインターフェイス ポインターを取得します。 |
| [GetDimensionCount](IMLOperatorTensor_GetDimensionCount.md) | テンソルで次元数を取得します。 |
| [GetShape](IMLOperatorTensor_GetShape.md) | テンソル内の次元のサイズを取得します。 |
| [GetTensorDataType](IMLOperatorTensor_GetTensorDataType.md) | テンソルのデータ型を取得します。 |
| [IsCpuData](IMLOperatorTensor_IsCpuData.md) | テンソルによって使用されるメモリが CPU を指定できるかどうかを示します。 |
| [IsDataInterface](IMLOperatorTensor_IsDataInterface.md) | かどうか、利用したテンソルの内容はインターフェイスの型、またはバイトのアドレス指定可能なメモリによって表されます。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
