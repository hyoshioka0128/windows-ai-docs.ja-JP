---
author: eliotcowley
title: ITensorNative インターフェイス
description: バイトまたは ID3D12Resource オブジェクトの配列として、ITensor にアクセスを提供します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、ITensorNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ITensorNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: cb64322047641d1dba4743605535dca4876b225f
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474119"
---
# <a name="itensornative-interface"></a>ITensorNative インターフェイス

アクセスできるように、 [ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)バイトの配列としてまたは[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)オブジェクト。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [GetBuffer](ITensorNative_GetBuffer.md) | バイト配列として利用したテンソルのバッファーを取得します。 |
| [GetD3D12Resource](ITensorNative_GetD3D12Resource.md) | として利用したテンソル バッファーを取得、 [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)します。 |

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../includes/get-help.md)]
