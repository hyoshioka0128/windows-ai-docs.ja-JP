---
author: eliotcowley
title: IMLOperatorTensor インターフェイス
description: カスタム演算子のカーネルの計算中に使用される利用したテンソルの表現。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: a26cd2eb5a1a4be45ff7077c265c972258bbf60d
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181654"
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

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
