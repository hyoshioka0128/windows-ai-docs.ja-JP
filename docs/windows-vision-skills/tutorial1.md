---
author: eliotcowley
title: ビジョン スキル UWP アプリケーションを作成します。
description: このチュートリアルで、UWP アプリにビジョンのスキルを統合します。
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: windows 10、windows の ai windows ビジョンのスキルを uwp
ms.localizationpriority: medium
ms.openlocfilehash: 75aa0082002dcc75277811f4d1d747d5e7ad64bb
ms.sourcegitcommit: 4ad0fea02000c8f6dbb9a919fb6ce1f435d0e8d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67334157"
---
# <a name="tutorial-create-a-windows-vision-skill-uwp-application"></a>チュートリアル:Windows のビジョンのスキルの UWP アプリケーションを作成します。

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

前の[チュートリアル](tutorial.md)、作成して、Windows のビジョンのスキルをパッケージ化する方法について説明しました。 ここで、ユニバーサル Windows プラットフォーム (UWP) アプリケーションを統合する方法について説明します。 使用できる完全なサンプルをダウンロードする[GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs)をどのようにしたらを参照してください。

このチュートリアルに関連性で見つかりますここ読み込みの詳細について *[VideoFrames](https://docs.microsoft.com/uwp/api/Windows.Media.VideoFrame)* 次のソースから。
- [既存*SoftwareBitmap*](https://docs.microsoft.com/uwp/api/windows.media.videoframe.createwithsoftwarebitmap#Windows_Media_VideoFrame_CreateWithSoftwareBitmap_Windows_Graphics_Imaging_SoftwareBitmap_)
- [イメージ ファイル](https://docs.microsoft.com/windows/uwp/audio-video-camera/imaging#create-a-softwarebitmap-from-an-image-file-with-bitmapdecoder)
- 使用してカメラ[FrameReader](https://docs.microsoft.com/windows/uwp/audio-video-camera/process-media-frames-with-mediaframereader)
- Microsoft.Toolkit を介してカメラ:[CameraPreview](https://docs.microsoft.com/windows/communitytoolkit/controls/camerapreview)、 [CameraHelper](https://docs.microsoft.com/windows/communitytoolkit/helpers/camerahelper)

---
## <a name="prerequisites"></a>前提条件

- 前のチュートリアルを完了[Windows ビジョン スキルを作成します。](tutorial.md)
---

## <a name="api-flow"></a>API のフロー
ここで説明されている API のフローを再確認、[重要な API の概念](important-api-concepts.md#APIFlow)具体的な一連のクラスのようになりましたが、ページC#します。 完全なサンプル コードは[GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/cs/Apps/FaceSentimentAnalysisApp_UWP/MainPage.xaml.cs)します。 

Windows のビジョン スキル API に関連するコードの行について説明します。 

+ インスタンスを作成、 [ISkillDescriptor][ISkillDescriptor]派生物

    ```csharp
    ...
    
    // member variable to hold the skill descriptor
    private FaceSentimentAnalyzerDescriptor m_skillDescriptor = null;
    
    ...
    
    // Instatiate skill descriptor to display details about the skill and populate UI
    m_skillDescriptor = new FaceSentimentAnalyzerDescriptor();

    ...
    ```

+ クエリを使用して利用可能な実行デバイス、 [ISKillDescriptor][ISKillDescriptor]インスタンス
    ```csharp
    ...
    
    // member variable to hold the available execution devices
    private IReadOnlyList<ISkillExecutionDevice> m_availableExecutionDevices = null;
    
    ...
    
    m_availableExecutionDevices = await m_skillDescriptor.GetSupportedExecutionDevicesAsync();

    ...
    ```

+ スキルを使用して、インスタンス化、 [ISKillDescriptor][ISKillDescriptor]インスタンスおよび、必要な[ISkillExecutionDevice][ISkillExecutionDevice]
    ```csharp
    ...
    
    // member variable to hold the skill
    private FaceSentimentAnalyzerSkill m_skill = null;
    
    ...
    
    // Initialize skill with the selected supported device
    m_skill = await m_skillDescriptor.CreateSkillAsync(m_availableExecutionDevices[UISkillExecutionDevices.SelectedIndex]) as FaceSentimentAnalyzerSkill;

    ...
    ```

+ バインド オブジェクトを使用して、スキルをインスタンス化、 [ISKill][ISKill]インスタンス
    ```csharp
    ...
    
    // member variable to hold the skill binding
    private FaceSentimentAnalyzerBinding m_binding = null;
    
    ...
    
   // Instantiate a binding object that will hold the skill's input and output resource
   m_binding = await m_skill.CreateSkillBindingAsync() as FaceSentimentAnalyzerBinding;

    ...
    ```

+ 入力、プリミティブ型を取得 (*VideoFrame*) し、対応するアクセスすることによって、バインディング オブジェクトにバインドする[ISkillFeature][ISkillFeature]名前を使用してインデックスを作成します。 このスキルを便利なメソッドの設定宣言*SetInputImage*
    ```csharp
    ...

    // Retrieve a VideoFrame from an image file
    VideoFrame frame = await LoadVideoFrameFromFilePickedAsync();

    ...

    // Update input image feature
    await m_binding.SetInputImageAsync(frame);

    ...
    ```
    この便利なメソッドは、バイパスする可能性があり、値をそのために直接 like 設定と同じ効果があります。

    ```csharp
    // Update input image feature
    await m_binding["InputImage"].SetFeatureValueAsync(frame);
    ```

+ バインド オブジェクト上で、スキルを実行します。
    ```csharp
    // Evaluate the binding
    await m_skill.EvaluateAsync(m_binding);
    ```

+ バインド オブジェクトから、出力のプリミティブを取得します。 このスキルがという名前の便利な get アクセス操作子プロパティを宣言することに注意してください。 *IsFaceFound*します。
    ```csharp
    // Retrieve results
    if (m_binding.IsFaceFound)
    {
        IReadOnlyList<float> scores = (m_binding["FaceSentimentScores"].FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
    }
    ```

    前のチュートリアルでは、以下に詳しく説明されているこの便利なメソッドは、バインドから直接出力機能を取得すると同じ効果を備え、ゼロでない値を検証しています。

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
