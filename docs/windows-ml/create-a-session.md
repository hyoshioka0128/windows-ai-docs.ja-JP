---
title: セッションを作成する
description: デバイスにモデルをバインドするために使用できるセッションを作成する方法について説明します。これにより、モデルを実行して評価することができます。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: feb1dd5e2837039ea573361ea338cbd8c387ebab
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156060"
---
# <a name="create-a-session"></a>セッションを作成する

[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)を読み込むと、モデルを実行して評価するデバイスにモデルをバインドする[LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession)が作成されます。

## <a name="choose-a-device"></a>デバイスの選択

セッションの作成時にデバイスを選択できます。 種類が[LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind)のデバイスを選択します。

* **[Default]**
    * 使用するデバイスをシステムが決定できるようにします。 現在、既定のデバイスは CPU です。
* **CPU**
    * 他のデバイスが使用可能な場合でも、CPU を使用します。
* **DirectX**
    * DirectX ハードウェアアクセラレーションデバイスを使用します。具体的には、 [IDXGIFactory1:: EnumAdapters1](https://docs.microsoft.com/windows/desktop/api/dxgi/nf-dxgi-idxgifactory1-enumadapters1)によって列挙される最初のアダプターです。
* **DirectXHighPerformance**
    * **DirectX**と同じですが、アダプターを列挙するときに[DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference)が使用されます。
* **DirectXMinPower**
    * **DirectX**と同じですが、アダプターを列挙するときに[DXGI_GPU_PREFERENCE_MINIMUM_POWER](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference)が使用されます。

デバイスを指定しない場合、システムは**既定値**を使用します。 **既定値**を使用することをお勧めします。これにより、将来的にシステムを選択できる柔軟性が得られます。

次のビデオでは、各デバイスの種類について詳しく説明します。

<br/>

> [!VIDEO https://www.youtube.com/embed/NM5CYUMMp-w]

## <a name="example"></a>例

次の例は、モデルとデバイスからセッションを作成する方法を示しています。

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
* 次の手順:[モデルを作成する](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
