---
author: eliotcowley
title: ITensorStaticsNative インターフェイス
description: ID3D12Resource を使用して ITensor オブジェクトの作成を有効にするファクトリ メソッドへのアクセスを提供します。
ms.author: elcowle
ms.date: 4/2/2019
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
ms.openlocfilehash: b10f44d7f43d62434dd4adbf770659b58088c6ad
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180094"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
