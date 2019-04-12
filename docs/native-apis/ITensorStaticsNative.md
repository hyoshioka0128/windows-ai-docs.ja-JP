---
author: eliotcowley
title: ITensorStaticsNative インターフェイス
description: ID3D12Resource を使用して ITensor オブジェクトの作成を有効にするファクトリ メソッドへのアクセスを提供します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、ITensorStaticsNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorStaticsNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 7c58025159e48f0cbaddccc45e9e86d97c054aa0
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473839"
---
# <a name="itensorstaticsnative-interface"></a>ITensorStaticsNative インターフェイス

作成を有効にするファクトリ メソッドへのアクセスを提供[ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)オブジェクトを使用して[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateFromD3D12Resource](ITensorStaticsNative_CreateFromD3D12Resource.md) | 利用したテンソル オブジェクトを作成します ([TensorFloat](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorfloat)、 [TensorInt32Bit](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.tensorint32bit)) からユーザーが指定した[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../includes/get-help.md)]
