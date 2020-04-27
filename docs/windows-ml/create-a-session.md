---
title: セッションを作成する
description: デバイスにモデルをバインドするために使用できるセッションを作成する方法について説明します。その後、このデバイスはモデルを実行して評価できます。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: c4b2e330efce5b0d5b7a2f5729adc94a97fb604e
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "80231592"
---
# <a name="create-a-session"></a>セッションを作成する

[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) を読み込んだ後、モデルを実行して評価するデバイスにモデルをバインドする [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession) を作成します。

## <a name="choose-a-device"></a>デバイスを選択する

セッションを作成するときにデバイスを選択できます。 種類が [LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind) のデバイスを選択します。

* **既定**
    * どのデバイスを使用するかをシステムが決定できるようにします。 現在、既定のデバイスは CPU です。
* **CPU**
    * 他のデバイスが使用可能な場合でも、CPU を使用します。
* **DirectX**
    * DirectX ハードウェア アクセラレータ デバイス、具体的には、[IDXGIFactory1::EnumAdapters1](https://docs.microsoft.com/windows/desktop/api/dxgi/nf-dxgi-idxgifactory1-enumadapters1) によって列挙される最初のアダプターを使用します。
* **DirectXHighPerformance**
    * **DirectX** と同じですが、アダプターを列挙するときに [DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference) を使用します。
* **DirectXMinPower**
    * **DirectX** と同じですが、アダプターを列挙するときに [DXGI_GPU_PREFERENCE_MINIMUM_POWER](https://docs.microsoft.com/windows/desktop/api/dxgi1_6/ne-dxgi1_6-dxgi_gpu_preference) を使用します。

デバイスを指定しないと、システムは **既定** を使用します。 将来、システムが自動的に選択できる柔軟性を得るために、**既定** を使用することをお勧めします。

次のビデオでは、デバイスの各種類について詳細に説明しています。

<br/>

> [!VIDEO https://www.youtube.com/embed/NM5CYUMMp-w]

## <a name="advanced-device-creation"></a>高度なデバイス作成

Windows AI では、呼び出し元が既に作成したデバイスの使用がサポートされています。  そうする際のいくつかのオプションと考慮事項があります。

* [CreateFromDirect3D11Device](https://docs.microsoft.com/en-us/uwp/api/windows.ai.machinelearning.learningmodeldevice.createfromdirect3d11device)。  既存の IDirect3DDevice が既にある場合は、これを使用します。  Windows AI は、同じアダプターを使用して ML ワークロードのために d3d12 デバイスを作成します。  これは、VideoFrame のために d3d11 デバイスを使用しているカメラがあり、LearningModelSession でも同じデバイスを使用する場合に役立ちます。  多くの場合、こうすることでメモリ コピーを回避できます。  注: VideoFrame のテンソル化は、Windows AI に含まれる唯一の d3d11 ワークロードです。  この機能を使用しない場合は、d3d11 デバイスを共有したり作成したりすることに利点はありません。
* [CreateFromD3D12CommandQueue (ネイティブ)](https://docs.microsoft.com/en-us/windows/ai/windows-ml/native-apis/ilearningmodeldevicefactorynative_createfromd3d12commandqueue)。  再利用したい d3d12 デバイスがある場合は、これを使用してください。  Windows AI は ML ワークロードに対してこのコマンド キューを使用します。   また、D3D11On12CreateDevice を使用して d3d11 デバイスを作成します。  これは必要な時だけ行われ、VideoFrame のテンソル化など、すべての d3d11 ワークロードで使用されます。  この新しいデバイスには、LearningModelDevice.Direct3D11Device プロパティを使用してアクセスできます。

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

* 前の手順: [モデルを読み込む](load-a-model.md)
* 次の手順:[モデルを作成する](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
