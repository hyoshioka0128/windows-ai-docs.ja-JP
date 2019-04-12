---
author: eliotcowley
title: WinML ネイティブ Api
description: このセクションには、WinML ネイティブ Api のドキュメントが含まれています。
ms.author: elcowle
ms.date: 10/23/2018
ms.topic: article
keywords: windows 10、windows の機械学習、WinML
ms.localizationpriority: medium
ms.openlocfilehash: 63aea791c4cf0aa4d09a0ed33a9dcf9c2be5dbdd
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473869"
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

[!INCLUDE [help](includes/get-help.md)]
