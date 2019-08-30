---
title: ビジョンスキル UWP アプリケーションを作成する
description: このチュートリアルに従って、ビジョンスキルを UWP アプリに統合します。
ms.date: 4/25/2019
ms.topic: article
keywords: windows 10、windows ai、windows ビジョンスキル、uwp
ms.localizationpriority: medium
ms.openlocfilehash: d6e5b42ab86b1317d90555b72895df747daf9206
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156957"
---
# <a name="tutorial-create-a-windows-vision-skill-uwp-application"></a>チュートリアル:Windows ビジョンスキル UWP アプリケーションを作成する

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 Microsoft は、ここで提供される情報に関して、明示または黙示を問わず、いかなる保証も行いません。

前の[チュートリアル](tutorial.md)では、Windows ビジョンスキルを作成してパッケージ化する方法を学習しました。 次に、これをユニバーサル Windows プラットフォーム (UWP) アプリケーションに統合する方法について説明します。 [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs)から入手できる完全なサンプルをダウンロードして、完了時にどのように表示されるかを確認できます。

このチュートリアルに関連性で見つかりますここ読み込みの詳細について *[VideoFrames](https://docs.microsoft.com/uwp/api/Windows.Media.VideoFrame)* 次のソースから。
- [既存の*ソフトウェアビットマップ*](https://docs.microsoft.com/uwp/api/windows.media.videoframe.createwithsoftwarebitmap#Windows_Media_VideoFrame_CreateWithSoftwareBitmap_Windows_Graphics_Imaging_SoftwareBitmap_)
- [イメージファイル](https://docs.microsoft.com/windows/uwp/audio-video-camera/imaging#create-a-softwarebitmap-from-an-image-file-with-bitmapdecoder)
- [FrameReader](https://docs.microsoft.com/windows/uwp/audio-video-camera/process-media-frames-with-mediaframereader)経由のカメラ
- Microsoft Toolkit を使用したカメラ:[CameraPreview](https://docs.microsoft.com/windows/communitytoolkit/controls/camerapreview)、 [CameraHelper](https://docs.microsoft.com/windows/communitytoolkit/helpers/camerahelper)

---
## <a name="prerequisites"></a>前提条件

- [独自の Windows ビジョンスキルの作成](tutorial.md)に関する前のチュートリアルを完了しています
---

## <a name="api-flow"></a>API フロー
ここでは、「 [api の重要な概念](important-api-concepts.md#APIFlow)」ページで説明した api フローについて説明C#しますが、ここではのクラスの具体的なセットを示します。 完全なサンプルコードは、 [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/cs/Apps/FaceSentimentAnalysisApp_UWP/MainPage.xaml.cs)で入手できます。

Windows ビジョンスキル API に関連するコード行について説明します。

+ Isの[記述子][ISkillDescriptor]の派生をインスタンス化する

    ```csharp
    ...

    // member variable to hold the skill descriptor
    private FaceSentimentAnalyzerDescriptor m_skillDescriptor = null;

    ...

    // Instatiate skill descriptor to display details about the skill and populate UI
    m_skillDescriptor = new FaceSentimentAnalyzerDescriptor();

    ...
    ```

+ [Isの記述子][ISKillDescriptor]インスタンスを使用して、使用可能な実行デバイスに対してクエリを実行します。
    ```csharp
    ...

    // member variable to hold the available execution devices
    private IReadOnlyList<ISkillExecutionDevice> m_availableExecutionDevices = null;

    ...

    m_availableExecutionDevices = await m_skillDescriptor.GetSupportedExecutionDevicesAsync();

    ...
    ```

+ [Iskilldescriptor][ISKillDescriptor]インスタンスと必要な[Isinstexecutiondevice][ISkillExecutionDevice]を使用してスキルをインスタンス化する
    ```csharp
    ...

    // member variable to hold the skill
    private FaceSentimentAnalyzerSkill m_skill = null;

    ...

    // Initialize skill with the selected supported device
    m_skill = await m_skillDescriptor.CreateSkillAsync(m_availableExecutionDevices[UISkillExecutionDevices.SelectedIndex]) as FaceSentimentAnalyzerSkill;

    ...
    ```

+ [Iskill][ISKill]インスタンスを使用して、スキルバインドオブジェクトをインスタンス化する
    ```csharp
    ...

    // member variable to hold the skill binding
    private FaceSentimentAnalyzerBinding m_binding = null;

    ...

   // Instantiate a binding object that will hold the skill's input and output resource
   m_binding = await m_skill.CreateSkillBindingAsync() as FaceSentimentAnalyzerBinding;

    ...
    ```

+ 入力プリミティブ (*Videoframe*) を取得し、名前を使用してインデックス付けされた対応する[isinput 機能][ISkillFeature]にアクセスして、バインドオブジェクトにバインドします。 このスキルでは、便利な set メソッド*SetInputImage*が宣言されていることに注意してください。
    ```csharp
    ...

    // Retrieve a VideoFrame from an image file
    VideoFrame frame = await LoadVideoFrameFromFilePickedAsync();

    ...

    // Update input image feature
    await m_binding.SetInputImageAsync(frame);

    ...
    ```
    この便宜的な方法は、次のように値を直接設定するのと同じ効果があります。

    ```csharp
    // Update input image feature
    await m_binding["InputImage"].SetFeatureValueAsync(frame);
    ```

+ バインドオブジェクトに対してスキルを実行する
    ```csharp
    // Evaluate the binding
    await m_skill.EvaluateAsync(m_binding);
    ```

+ バインドオブジェクトから出力プリミティブを取得します。 このスキルでは、 *IsFaceFound*という便利な getter プロパティが宣言されていることに注意してください。
    ```csharp
    // Retrieve results
    if (m_binding.IsFaceFound)
    {
        IReadOnlyList<float> scores = (m_binding["FaceSentimentScores"].FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
    }
    ```

    前のチュートリアルで説明したように、この便利な方法は、バインディングから直接出力機能を取得し、その値が0ではないことを検証するのと同じ効果があります。

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
