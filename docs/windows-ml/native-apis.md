---
author: eliotcowley
title: WinML ネイティブ Api
description: このセクションには、WinML ネイティブ Api のドキュメントが含まれています。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows の機械学習、WinML
ms.localizationpriority: medium
ms.openlocfilehash: 0da51c115e7f951609122dc0df88d82d82425924
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181884"
---
# <a name="winml-native-apis"></a>WinML ネイティブ Api

Windows Machine Learning のネイティブ Api にある**windows.ai.machinelearning.native.h**します。

## <a name="apis"></a>API

次に WinML のネイティブ Api の構文と説明の一覧を示します。

### <a name="interfaces"></a>インターフェイス

| 名前 | 説明 |
|------|-------------|
| [ILearningModelDeviceFactoryNative](native-apis/ILearningModelDeviceFactoryNative.md) | 作成を有効にするファクトリ メソッドへのアクセスを提供[ILearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)オブジェクトを使用して[ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)します。 |
| [ITensorNative](native-apis/ITensorNative.md) | アクセスできるように、 [ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)バイトの配列としてまたは[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)オブジェクト。 |
| [ITensorStaticsNative](native-apis/ITensorStaticsNative.md) | 作成を有効にするファクトリ メソッドへのアクセスを提供[ITensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)オブジェクトを使用して[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)します。 |

### <a name="structures"></a>構造体

| 名前 | 説明 |
|------|-------------|
| [ILearningModelOperatorProviderNative](native-apis/ILearningModelOperatorProviderNative.md) | アクセスを提供します。 [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md)カスタム演算子の登録を含むオブジェクト。 |

[!INCLUDE [help](../includes/get-help.md)]
