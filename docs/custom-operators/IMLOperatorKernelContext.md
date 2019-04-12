---
author: eliotcowley
title: IMLOperatorKernelContext インターフェイス
description: カーネルの計算中は、演算子の使用状況に関する情報を提供します。
ms.author: elcowle
ms.date: 11/8/2018
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
ms.openlocfilehash: 08accb1a8a1b0c9d2fb2f85c1e76034508bc6de7
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474669"
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

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
