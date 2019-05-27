---
author: eliotcowley
title: ILearningModelDeviceFactoryNative インターフェイス
description: ID3D12CommandQueue を使用して ILearningModelDevice オブジェクトの作成を有効にするファクトリ メソッドへのアクセスを提供します。
ms.author: elcowle
ms.date: 4/2/2019
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、ILearningModelDeviceFactoryNative
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- ILearningModelDeviceFactoryNative
api_location:
- windows.ai.machinelearning.native.h
ms.openlocfilehash: 035ff6dd7e765dcf1f2f21382eb6c488bdb66f63
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181874"
---
# <a name="ilearningmodeldevicefactorynative-interface"></a>ILearningModelDeviceFactoryNative インターフェイス

作成を有効にするファクトリ メソッドへのアクセスを提供[ILearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)オブジェクトを使用して[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateFromD3D12CommandQueue](ILearningModelDeviceFactoryNative_CreateFromD3D12CommandQueue.md) | 作成、 [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)推論を実行するユーザー指定の[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | windows.ai.machinelearning.native.h |

[!INCLUDE [help](../../includes/get-help.md)]
