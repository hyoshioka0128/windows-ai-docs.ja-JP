---
title: ビジョン スキル UWP アプリケーションを作成する
description: このチュートリアルに従って、ビジョン スキルを UWP アプリに統合します。
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10、Windows AI、Windows Vision Skills、UWP
ms.localizationpriority: medium
ms.openlocfilehash: d6e5b42ab86b1317d90555b72895df747daf9206
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156957"
---
# <a name="tutorial-create-a-windows-vision-skill-uwp-application"></a>チュートリアル: Windows Vision Skills UWP アプリケーションを作成する

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

前の[チュートリアル](tutorial.md)では、Windows Vision Skills を作成およびパッケージ化する方法を学習しました。 ここでは、それをユニバーサル Windows プラットフォーム (UWP) アプリケーションに統合する方法を学習します。 完了したときにそれがどのようになるかを確認するには、[GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs) で入手できる完全なサンプルをダウンロードできます。

また、このチュートリアルに関連して、次のソースからの *[VideoFrames](https://docs.microsoft.com/uwp/api/Windows.Media.VideoFrame)* の読み込みに関するより詳細情報をここで見つけることができます。
- [既存の *SoftwareBitmap*](https://docs.microsoft.com/uwp/api/windows.media.videoframe.createwithsoftwarebitmap#Windows_Media_VideoFrame_CreateWithSoftwareBitmap_Windows_Graphics_Imaging_SoftwareBitmap_)
- [イメージ ファイル](https://docs.microsoft.com/windows/uwp/audio-video-camera/imaging#create-a-softwarebitmap-from-an-image-file-with-bitmapdecoder)
- [FrameReader](https://docs.microsoft.com/windows/uwp/audio-video-camera/process-media-frames-with-mediaframereader) 経由のカメラ
- Microsoft.Toolkit 経由のカメラ: [CameraPreview](https://docs.microsoft.com/windows/communitytoolkit/controls/camerapreview)、[CameraHelper](https://docs.microsoft.com/windows/communitytoolkit/helpers/camerahelper)

---
## <a name="prerequisites"></a>前提条件

- [独自の Windows Vision Skills の作成](tutorial.md)に関する前のチュートリアルを完了していること
---

## <a name="api-flow"></a>API フロー
「[重要な API の概念](important-api-concepts.md#APIFlow)」のページで説明されている API フローを再度参照しますが、今回は C# の具体的なクラス セットを使用します。 完全なサンプル コードは、[GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/cs/Apps/FaceSentimentAnalysisApp_UWP/MainPage.xaml.cs) で入手できます。

Windows Vision Skills API に関連する次のコード行について説明します。

+ [ISkillDescriptor][ISkillDescriptor] 派生クラスをインスタンス化します。

    ```csharp
    ...

    // member variable to hold the skill descriptor
    private FaceSentimentAnalyzerDescriptor m_skillDescriptor = null;

    ...

    // Instatiate skill descriptor to display details about the skill and populate UI
    m_skillDescriptor = new FaceSentimentAnalyzerDescriptor();

    ...
    ```

+ [ISKillDescriptor][ISKillDescriptor] インスタンスを使用して、使用可能な実行デバイスに対してクエリを実行します。
    ```csharp
    ...

    // member variable to hold the available execution devices
    private IReadOnlyList<ISkillExecutionDevice> m_availableExecutionDevices = null;

    ...

    m_availableExecutionDevices = await m_skillDescriptor.GetSupportedExecutionDevicesAsync();

    ...
    ```

+ [ISKillDescriptor][ISKillDescriptor] インスタンスと目的の [ISkillExecutionDevice][ISkillExecutionDevice] を使用してスキルをインスタンス化します。
    ```csharp
    ...

    // member variable to hold the skill
    private FaceSentimentAnalyzerSkill m_skill = null;

    ...

    // Initialize skill with the selected supported device
    m_skill = await m_skillDescriptor.CreateSkillAsync(m_availableExecutionDevices[UISkillExecutionDevices.SelectedIndex]) as FaceSentimentAnalyzerSkill;

    ...
    ```

+ [ISKill][ISKill] インスタンスを使用してスキル バインディング オブジェクトをインスタンス化します。
    ```csharp
    ...

    // member variable to hold the skill binding
    private FaceSentimentAnalyzerBinding m_binding = null;

    ...

   // Instantiate a binding object that will hold the skill's input and output resource
   m_binding = await m_skill.CreateSkillBindingAsync() as FaceSentimentAnalyzerBinding;

    ...
    ```

+ 入力プリミティブ (*VideoFrame*) を取得し、その名前でインデックスが作成された対応する [ISkillFeature][ISkillFeature] にアクセスすることによって、それをバインディング オブジェクトにバインドします。 このスキルが簡易設定メソッド *SetInputImage* を宣言することに注意してください。
    ```csharp
    ...

    // Retrieve a VideoFrame from an image file
    VideoFrame frame = await LoadVideoFrameFromFilePickedAsync();

    ...

    // Update input image feature
    await m_binding.SetInputImageAsync(frame);

    ...
    ```
    この簡易メソッドはバイパスすることができ、次のように、値を直接設定するのと同じ効果があります。

    ```csharp
    // Update input image feature
    await m_binding["InputImage"].SetFeatureValueAsync(frame);
    ```

+ バインディング オブジェクトでスキルを実行します。
    ```csharp
    // Evaluate the binding
    await m_skill.EvaluateAsync(m_binding);
    ```

+ バインディング オブジェクトから出力プリミティブを取得します。 このスキルが *IsFaceFound* という名前の簡易 getter プロパティを宣言することに注意してください。
    ```csharp
    // Retrieve results
    if (m_binding.IsFaceFound)
    {
        IReadOnlyList<float> scores = (m_binding["FaceSentimentScores"].FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
    }
    ```

    前のチュートリアルや下で詳細に説明しているように、この簡易メソッドは、バインドから出力機能を直接取得し、その値が 0 でないことを検証するのと同じ効果があります。

    ```csharp
    public bool FaceSentimentAnalyzerBinding.IsFaceFound
    {
        get
        {
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue("FaceRectangle", out feature))
            {
                var faceRect = (feature.FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
                return !(faceRect[0] == 0.0f &&
                    faceRect[1] == 0.0f &&
                    faceRect[2] == 0.0f &&
                    faceRect[3] == 0.0f);
            }
            else
            {
                return false;
            }
        }
    ```



[!INCLUDE [help](../includes/get-help-vision.md)]

[SkillInterfacePreview]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview

[ISkillDescriptor]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor

[ISkill]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill

[ISkillBinding]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding

[ISkillExecutionDevice]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice

[ISkillFeature]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature

[ISkillFeatureValue]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue
