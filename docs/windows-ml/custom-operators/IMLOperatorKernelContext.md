---
title: IMLOperatorKernelContext インターフェイス
description: カーネルが計算されているときのオペレーターの使用状況に関する情報を提供します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Imloperatorカーネルコンテキスト
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: c1358ad70c4807c45a3ad6b130c770fe5bac82a5
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157206"
---
# <a name="imloperatorkernelcontext-interface"></a>IMLOperatorKernelContext インターフェイス

カーネルが計算されているときのオペレーターの使用状況に関する情報を提供します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [AllocateTemporaryData](IMLOperatorKernelContext_AllocateTemporaryData.md) | [Imloperatorkernel:: Compute](IMLOperatorKernel_Compute.md)の呼び出し中に、中間メモリとして使用できる一時データを割り当てます。 |
| [GetExecutionInterface](IMLOperatorKernelContext_GetExecutionInterface.md) | カーネルの種類によってサポートされるインターフェイスが異なるオブジェクトを返します。 |
| [GetInputTensor](IMLOperatorKernelContext_GetInputTensor.md) | 指定したインデックス位置にある演算子によって入力された入力を取得します。 |
| [Getoutputuint32_t (または、Imloperator、* *)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor1) | 指定したインデックス位置にある演算子によって取得された出力を取得します。 |
| [Getoutputuint32_t (uint32_t、const uint32_t *、Imloperatorall * *)](IMLOperatorKernelContext_GetOutputTensor.md#GetOutputTensor2) | 図形の宣言中に、指定したインデックス位置にある演算子によって取得された出力を取得します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
