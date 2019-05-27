---
author: eliotcowley
title: セッションを作成する
description: 実行とモデルを評価し、デバイスにモデルをバインドするために使用できるセッションを作成する方法について説明します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 918300b23a2d2c3a8c80307725722bba05bfaa42
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180434"
---
# <a name="create-a-session"></a>セッションを作成する

読み込んだら、 [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)、作成する、 [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession)を実行し、モデルを評価しているデバイスにモデルをバインドします。

## <a name="choose-a-device"></a>デバイスを選択します。

セッションを作成するときに、デバイスを選択することができます。 型のデバイスを選択した[LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind):

* **Default**
    * システムが使用するデバイスを決定できるようにします。 現時点では、既定のデバイスには、CPU です。
* **CPU**
    * その他のデバイスが使用可能な場合でも、CPU を使用します。
* **DirectX**
    * DirectX ハードウェア高速化デバイス、具体的には、最初のアダプターによって列挙を使用して[IDXGIFactory1::EnumAdapters1](https://docs.microsoft.com/windows/desktop/api/dxgi/nf-dxgi-idxgifactory1-enumadapters1)します。
* **DirectXHighPerformance**
    * 同じ**DirectX**が使用されますが、 [DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference)アダプターを列挙する場合。
* **DirectXMinPower**
    * 同じ**DirectX**が使用されますが、 [DXGI_GPU_PREFERENCE_MINIMUM_POWER](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference)アダプターを列挙する場合。

デバイスを指定しない場合、システムは**既定**します。 使用することをお勧めします。**既定**システムが、将来の選択の柔軟性を得る。

次のビデオでは、デバイスの種類はそれぞれの詳細に移動します。

<br/>

> [!VIDEO https://www.youtube.com/embed/NM5CYUMMp-w]

## <a name="example"></a>例

次の例では、モデルと、デバイスからセッションを作成する方法を示します。

```cs
private void CreateSession(LearningModel model, LearningModelDeviceKind kind) 
{
    // Create the evaluation session with the model and device
    LearningModelSession session = 
        new LearningModelSession(model, new LearningModelDevice(kind));
}
```

## <a name="see-also"></a>関連項目

* 先の：[モデルを読み込む](load-a-model.md)
* 次に：[モデルをバインドします。](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
