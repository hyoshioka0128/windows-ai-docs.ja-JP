---
author: eliotcowley
title: IMLOperatorKernelContext インターフェイス
description: カーネルの計算中は、演算子の使用状況に関する情報を提供します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を IMLOperatorKernelContext
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3e6708a905d3ff9277fa80793329eb149fbafb2c
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181174"
---
# <a name="imloperatorkernelcontext-interface"></a>IMLOperatorKernelContext インターフェイス

カーネルの計算中は、演算子の使用状況に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [AllocateTemporaryData](IMLOperatorKernelContext_AllocateTemporaryData.md) | 呼び出しの間の中間メモリとして使用できる一時的なデータを割り当てます[IMLOperatorKernel::Compute](IMLOperatorKernel_Compute.md)します。 |
| [GetExecutionInterface](IMLOperatorKernelContext_GetExecutionInterface.md) | カーネルの種類に基づいて、サポートされているインターフェイスが異なるオブジェクトを返します。 |
| [GetInputTensor](IMLOperatorKernelContext_GetInputTensor.md) | 指定したインデックス位置にある演算子の入力 tensor を取得します。 |
| [GetOutputTensor(uint32_t, IMLOperatorTensor**)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor1) | 指定したインデックス位置にある演算子の出力 tensor を取得します。 |
| [GetOutputTensor(uint32_t, uint32_t, const uint32_t*, IMLOperatorTensor**)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor2) | 指定したインデックス位置の形状を宣言するときに、演算子の出力 tensor を取得します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
