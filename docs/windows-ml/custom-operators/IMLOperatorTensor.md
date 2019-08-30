---
title: Imloperator、インターフェイス
description: カスタム演算子カーネルの計算中に使用される、オートの表現。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Imloperator、
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c5cda4b43175cb78372abc1211083ab9d3232a00
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157790"
---
# <a name="imloperatortensor-interface"></a>Imloperator、インターフェイス

カスタム演算子カーネルの計算中に使用される、オートの表現。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetData](IMLOperatorTensor_GetData.md) | は、その後、またはに対して、バイトでアドレス指定可能なメモリへのポインターを返します。 |
| [GetDataInterface](IMLOperatorTensor_GetDataInterface.md) | 既存ののインターフェイスポインターを取得します。 |
| [GetDimensionCount](IMLOperatorTensor_GetDimensionCount.md) | の次元数を取得します。 |
| [GetShape](IMLOperatorTensor_GetShape.md) | の次元のサイズを取得します。 |
| [GetTensorDataType](IMLOperatorTensor_GetTensorDataType.md) | のデータ型を取得します。 |
| [IsCpuData](IMLOperatorTensor_IsCpuData.md) | この値によって使用されるメモリが CPU でアドレス指定可能かどうかを示します。 |
| [IsDataInterface](IMLOperatorTensor_IsDataInterface.md) | すべての内容がインターフェイス型で表されるか、またはバイトアドレス可能なメモリで表されるかを示します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
