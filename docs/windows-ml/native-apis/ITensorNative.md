---
author: eliotcowley
title: ITensorNative インターフェイス
description: バイトまたは ID3D12Resource オブジェクトの配列として、ITensor にアクセスを提供します。
ms.author: elcowle
ms.date: 4/2/2019
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
ms.openlocfilehash: 2427a5916244e72b19c95a78d1b02ee425c357db
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180134"
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
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
