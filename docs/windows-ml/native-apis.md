---
title: WinML ネイティブ Api
description: このセクションには、WinML ネイティブ Api のドキュメントが含まれています。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML
ms.localizationpriority: medium
ms.openlocfilehash: 6fee01e711fb94681a61914dcc4ec317577689b9
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156587"
---
# <a name="winml-native-apis"></a>WinML ネイティブ Api

Windows Machine Learning のネイティブ Api は、 **windows の ai**...。

## <a name="apis"></a>API

次に、WinML ネイティブ Api とその構文と説明を示します。

### <a name="interfaces"></a>インターフェイス

| 名前 | 説明 |
|------|-------------|
| [ILearningModelDeviceFactoryNative](native-apis/ILearningModelDeviceFactoryNative.md) | [ID3D12CommandQueue](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)を使用して[ILearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice)オブジェクトを作成できるようにするファクトリメソッドへのアクセスを提供します。 |
| [ITensorNative](native-apis/ITensorNative.md) | バイトまたは[ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)オブジェクトの配列として[itensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)にアクセスできるようにします。 |
| [ITensorStaticsNative](native-apis/ITensorStaticsNative.md) | [ID3D12Resource](https://docs.microsoft.com/windows/desktop/api/d3d12/nn-d3d12-id3d12resource)を使用して[itensor](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.itensor)オブジェクトを作成できるようにするファクトリメソッドへのアクセスを提供します。 |

### <a name="structures"></a>構造体

| 名前 | 説明 |
|------|-------------|
| [ILearningModelOperatorProviderNative](native-apis/ILearningModelOperatorProviderNative.md) | カスタムオペレーター登録を含む[Imloperatorregistry](custom-operators/IMLOperatorRegistry.md)オブジェクトへのアクセスを提供します。 |

[!INCLUDE [help](../includes/get-help.md)]
