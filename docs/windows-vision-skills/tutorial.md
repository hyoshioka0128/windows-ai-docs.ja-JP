---
author: eliotcowley
title: ビジョン スキルの作成 (C#/C++)
description: このチュートリアルで、独自の Windows のビジョンのスキルを作成する方法について説明します。
ms.author: elcowle
ms.date: 5/10/2019
ms.topic: article
keywords: windows 10、windows の ai windows vision スキル
ms.localizationpriority: medium
ms.openlocfilehash: af0e6a9ee2fe80531a41a0f2722f1a8c8b9c723c
ms.sourcegitcommit: 4ad0fea02000c8f6dbb9a919fb6ce1f435d0e8d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67334106"
---
# <a name="tutorial-create-your-own-windows-vision-skill-c"></a>チュートリアル:Windows のビジョン スキルの作成 (C#)

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

このチュートリアルを拡張することによって、Windows のビジョンのスキルでソリューションをラップする方法を示しています、ビジョンのカスタム ソリューションを既にある場合、 [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] API のベースします。

次を利用している顔センチメント アナライザー スキルを構築してみましょう。

- [Windows.Media.FaceAnalysis](https://docs.microsoft.com/uwp/api/windows.media.faceanalysis)と[Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) Api
- 画像の顔から感情を推測 ONNX 形式での machine learning モデル

このスキルが必要です。

- 入力の画像

出力します。

- 利用したテンソル各センチメントの範囲 [0, 1] のスコアの値を単精度の評価します。
- 顔の境界ボックスの相対座標を定義する範囲 [0, 1] の値を float の利用したテンソル: 左側 (x, y)、(x, y) の一番上、右 (x, y)、および下 (x, y)

![例 FaceSentimentAnalysis スキルの入力と出力のダイアグラム](../images/vision-skills-FaceSentimentAnalysis.png)

完全なソース コード、C#とC++/サンプルの GitHub リポジトリでこの例の WinRT バージョンが使用可能な。

- [C#例のスキル](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs)
- [C++/WinRT の例のスキル](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp)

このチュートリアルをします。

1. [メイン インターフェイスを実装する](#CreateMainClasses)Windows ビジョンのスキルに必要な
2. [.Nuspec を作成する](#CreateNuspec)NuGet パッケージを生成するには
3. [難読化して、deobfuscating](#Obfuscation)ファイルをコンテンツを非表示

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (または Visual Studio 2017 バージョン 15.7.4 またはそれ以降)
- Windows 10、1809 またはそれ以降のバージョン
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)、1809 またはそれ以降のバージョン
- [Microsoft.AI.Skills.SkillInterfacePreview NuGet パッケージ](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/)

## 1. 作成し、スキルのメイン クラスの実装 <a name="CreateMainClasses"></a>

最初に、主なスキルのクラスを実装する必要があります (を参照してください[重要な API の概念](important-api-concepts.md)詳細)。

- [ISkillDescriptor](#ISkillDescriptor)
- [ISkillBinding](#ISkillBinding)
- [ISkill](#ISkill)

Visual Studio でカスタム ビジョン ソリューションを開きます。

### a. ISkillDescriptor <a name="ISkillDescriptor"></a>

作成し、スキル記述子クラスから継承された実装[ISkillDescriptor] [ ISkillDescriptor]スキルに関する情報を (CPU、GPU、およびなど) の実行がサポートされているデバイスの一覧を示しますおよびとして機能しますスキルのファクトリ オブジェクト。

1. インポート、 [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview]名前空間、クラスから派生したもので、 [ISkillDescriptor] [ ISkillDescriptor]インターフェイスです。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerDescriptor : ISkillDescriptor
    {
        ...
    }
    ```

2. 入力と出力が必要なスキルの説明を保持する 2 つのメンバー変数を作成します。 次に、記述子の 's コンス トラクター、塗りつぶしに適宜記述子の入力と出力の機能と、ベースで公開されるすべてのプロパティに値を割り当てるインターフェイスについて説明します、スキルです。

    ```csharp
    ...
    // Member variables to hold input and output descriptions
    private List<ISkillFeatureDescriptor> m_inputSkillDesc;
    private List<ISkillFeatureDescriptor> m_outputSkillDesc;

    // Properties required by the interface
    public string Description { get; private set; }
    public Guid Id { get; }
    public IReadOnlyList<ISkillFeatureDescriptor> InputFeatureDescriptors => m_inputSkillDesc;
    public IReadOnlyDictionary<string, string> Metadata => null;
    public string Name { get; private set; }
    public IReadOnlyList<ISkillFeatureDescriptor> OutputFeatureDescriptors => m_outputSkillDesc;
    public SkillVersion Version { get; }

    // Constructor
    public FaceSentimentAnalyzerDescriptor()
    {
        Name = "FaceSentimentAnalyzer";

        Description = "Finds a face in the image and infers its predominant sentiment from a set of 8 possible labels";

        // Unique ID {F8D275CE-C244-4E71-8A39-57335D291388}
        Id = new Guid(0xf8d275ce, 0xc244, 0x4e71, 0x8a, 0x39, 0x57, 0x33, 0x5d, 0x29, 0x13, 0x88);

        Version = SkillVersion.Create(
                    0,  // major version
                    1,  // minor version
                    "Contoso Developer", // Author name
                    "Contoso Publishing" // Publisher name
                    );

        // Describe input feature
        m_inputSkillDesc = new List<ISkillFeatureDescriptor>();
        m_inputSkillDesc.Add(
            new SkillFeatureImageDescriptor(
                "InputImage", // skill input feature name
                "the input image onto which the sentiment analysis runs",
                true, // isRequired (since this is an input, it is required to be bound before the evaluation occurs)
                -1, // width
                -1, // height
                -1, // maxDimension
                BitmapPixelFormat.Nv12,
                BitmapAlphaMode.Ignore)
        );

        // Describe first output feature
        m_outputSkillDesc = new List<ISkillFeatureDescriptor>();
        m_outputSkillDesc.Add(
            new SkillFeatureTensorDescriptor(
                "FaceRectangle", // skill output feature name
                "a face bounding box in relative coordinates (left, top, right, bottom)",
                false, // isRequired (since this is an output, it automatically get populated after the evaluation occurs)
                new List<long>() { 4 }, // tensor shape
                SkillElementKind.Float)
            );

        // Describe second output feature
        m_outputSkillDesc.Add(
            new SkillFeatureTensorDescriptor(
                FaceSentimentScores, // skill output feature name
                "the prediction score for each class",
                false, // isRequired (since this is an output, it automatically get populated after the evaluation occurs)
                new List<long>() { 1, 8 }, // tensor shape
                SkillElementKind.Float)
            );
    }

    ```

3. スキルを実行するデバイスを利用可能なサポートされている実行を検索し、コンシューマーに返しますに必要なメソッドを実装します。 ここで私たちは、CPU と D3D バージョン 12 をサポートしているすべての DirectX デバイス返す以降。

    ```csharp
    public IAsyncOperation<IReadOnlyList<ISkillExecutionDevice>> GetSupportedExecutionDevicesAsync()
    {
        return AsyncInfo.Run(async (token) =>
        {
            return await Task.Run(() =>
            {
                var result = new List<ISkillExecutionDevice>();

                // Add CPU as supported device
                result.Add(SkillExecutionDeviceCPU.Create());

                // Retrieve a list of DirectX devices available on the system and filter them by keeping only the ones that support DX12+ feature level
                var devices = SkillExecutionDeviceDirectX.GetAvailableDirectXExecutionDevices();
                var compatibleDevices = devices.Where((device) => (device as SkillExecutionDeviceDirectX).MaxSupportedFeatureLevel >= D3DFeatureLevelKind.D3D_FEATURE_LEVEL_12_0);
                result.AddRange(compatibleDevices);

                return result as IReadOnlyList<ISkillExecutionDevice>;
            });
        });

    ```

4. スキルをインスタンス化するため、必要なメソッドを実装します。

    - うち 1 つは、使用可能な最適なデバイスを選択します。

        ```csharp
        public IAsyncOperation<ISkill> CreateSkillAsync()
        {
            return AsyncInfo.Run(async (token) =>
            {
                // Retrieve the available execution devices
                var supportedDevices = await GetSupportedExecutionDevicesAsync();
                ISkillExecutionDevice deviceToUse = supportedDevices.First();

                // Either use the first device returned (CPU) or the highest performing GPU
                int powerIndex = int.MaxValue;
                foreach (var device in supportedDevices)
                {
                    if (device.ExecutionDeviceKind == SkillExecutionDeviceKind.Gpu)
                    {
                        var directXDevice = device as SkillExecutionDeviceDirectX;
                        if (directXDevice.HighPerformanceIndex < powerIndex)
                        {
                            deviceToUse = device;
                            powerIndex = directXDevice.HighPerformanceIndex;
                        }
                    }
                }
                return await CreateSkillAsync(deviceToUse);
            });
        }
        ```

    - 他は、指定された実行デバイスを使用します。

        ```csharp
        public IAsyncOperation<ISkill> CreateSkillAsync(ISkillExecutionDevice executionDevice)
        {
            return AsyncInfo.Run(async (token) =>
            {
                // Create a skill instance with the executionDevice supplied
                var skillInstance = await FaceSentimentAnalyzerSkill.CreateAsync(this, executionDevice);

                return skillInstance as ISkill;
            });
        }
        ```

### b. **ISkillBinding** <a name="ISkillBinding"></a>

作成し、スキルから継承されるクラスにバインド実装[ISkillBinding] [ ISkillBinding]およびスキルによって生成される入力と出力の変数を含むインターフェイス。

1. インポート、 [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview]名前空間、クラスから派生したもので、 [ISkillBinding] [ ISkillBinding]インターフェイスとその必要なコレクションを入力します。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerBinding : IReadOnlyDictionary<string, ISkillFeature>, ISkillBinding
    {
        ...

    ```

2. まず 2 つのメンバー変数を作成します。

    - 1 つのヘルパー クラスは、 [VisionSkillBindingHelper] [ VisionSkillBindingHelper]機能が"InputImage"を名前付き入力のイメージを保持する基本インターフェイスで提供します。

    ```csharp
    private VisionSkillBindingHelper m_bindingHelper = null;
    ```

    - 他には、スキル クラスで後で、コンス トラクターに引数として指定された、LearningModelSession に渡すために使用する LearningModelBinding は保持されます。

    ```csharp
    // WinML related member variables
    internal LearningModelBinding m_winmlBinding = null;
    ```

    必要なプロパティを宣言します。

    ```csharp
    // ISkillBinding
    public ISkillExecutionDevice Device => m_bindingHelper.Device;

    // IReadOnlyDictionary
    public bool ContainsKey(string key) => m_bindingHelper.ContainsKey(key);
    public bool TryGetValue(string key, out ISkillFeature value) => m_bindingHelper.TryGetValue(key, out value);
    public ISkillFeature this[string key] => m_bindingHelper[key];
    public IEnumerable<string> Keys => m_bindingHelper.Keys;
    public IEnumerable<ISkillFeature> Values => m_bindingHelper.Values;
    public int Count => m_bindingHelper.Count;
    public IEnumerator<KeyValuePair<string, ISkillFeature>> GetEnumerator() => m_bindingHelper.AsEnumerable().GetEnumerator();
    IEnumerator IEnumerable.GetEnumerator() => m_bindingHelper.AsEnumerable().GetEnumerator();
    ```

    およびコンス トラクターを実装します。 コンス トラクターは*内部*; で、パラダイム、ISkillBinding インスタンスは、スキルによって作成され、スタンドアロンのコンス トラクターを公開する必要があります。

    ```csharp
     // Constructor
    internal FaceSentimentAnalyzerBinding(
        ISkillDescriptor descriptor,
        ISkillExecutionDevice device,
        LearningModelSession session)
    {
        m_bindingHelper = new VisionSkillBindingHelper(descriptor, device);

        // Create WinML binding
        m_winmlBinding = new LearningModelBinding(session);
    }
    ```

3. スキルでセンチメントの種類の出力の読み取りを容易にする列挙型を作成します。

    ```csharp
    /// Defines the set of possible emotion label scored by this skill
    public enum SentimentType
    {
        neutral = 0,
        happiness,
        surprise,
        sadness,
        anger,
        disgust,
        fear,
        contempt
    };
    ```

4. Get を軽減し、操作をバインディングに設定されるオプションの追加メソッドを実装します。

    ```csharp
    /// Returns whether or not a face is found given the bound outputs
    public bool IsFaceFound
    {
        get
        {
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue(FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACERECTANGLE, out feature))
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
    }

    /// Returns the sentiment with the highest score
    public SentimentType PredominantSentiment
    {
        get
        {
            SentimentType predominantSentiment = SentimentType.neutral;
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue(FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACESENTIMENTSCORES, out feature))
            {
                var faceSentimentScores = (feature.FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();

                float maxScore = float.MinValue;
                for (int i = 0; i < faceSentimentScores.Count; i++)
                {
                    if (faceSentimentScores[i] > maxScore)
                    {
                        predominantSentiment = (SentimentType)i;
                        maxScore = faceSentimentScores[i];
                    }
                }
            }

            return predominantSentiment;
        }
    }

    /// Returns the face rectangle
    public IReadOnlyList<float> FaceRectangle
    {
        get
        {
            ISkillFeature feature = null;
            if (m_bindingHelper.TryGetValue(FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACERECTANGLE, out feature))
            {
                return (feature.FeatureValue as SkillFeatureTensorFloatValue).GetAsVectorView();
            }
            else
            {
                return null;
            }
        }
    }
    ```

### c. **ISkill** <a name="ISkill"></a>

作成してから継承されるスキル クラスを実装する[ISkill] [ ISkill]スキル ロジックを実行し、与えられた一連の入力の出力を生成するインターフェイスです。 ISkillBinding 派生クラスのファクトリ オブジェクトとしても機能します。

1. インポート、 [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview]名前空間、クラスから派生したもので、 [ISkill] [ ISkill]インターフェイス。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerSkill : ISkill
    {
        ...
    ```

2. まず 2 つのメンバー変数を作成します。

    - 入力の画像で顔を検索する FaceDetector を保持するために 1 つです。

    ```csharp
    private FaceDetector m_faceDetector = null;
    ```

    - 別の感情分析モデルの評価に使用される LearningModelSession を保持するには:

    ```csharp
    private LearningModelSession m_winmlSession = null;
    ```

    必要なプロパティを宣言します。

    ```csharp
    public ISkillDescriptor SkillDescriptor { get; private set; }
    public ISkillExecutionDevice Device { get; private set; }
    ```

    およびコンス トラクターと静的ファクトリ メソッドを実装します。 コンス トラクターは*プライベート*ファクトリ メソッドが*内部*; で、パラダイム、ISkill インスタンス スキル記述子によって作成され、スタンドアロンのコンス トラクターを公開する必要があります:

    ```csharp
     // Constructor
    private FaceSentimentAnalyzerSkill(
            ISkillDescriptor description,
            ISkillExecutionDevice device)
    {
        SkillDescriptor = description;
        Device = device;
    }

    // ISkill Factory method
    internal static IAsyncOperation<FaceSentimentAnalyzerSkill> CreateAsync(
        ISkillDescriptor descriptor,
        ISkillExecutionDevice device)
    {
        return AsyncInfo.Run(async (token) =>
        {
            // Create instance
            var skillInstance = new FaceSentimentAnalyzerSkill(descriptor, device);

            // Instantiate the FaceDetector
            skillInstance.m_faceDetector = await FaceDetector.CreateAsync();

            // Load ONNX model and instantiate LearningModel
            var modelFile = await StorageFile.GetFileFromApplicationUriAsync(new Uri($"ms-appx:///Contoso.FaceSentimentAnalyzer/emotion_ferplus.onnx"));
            var winmlModel = LearningModel.LoadFromFilePath(modelFile.Path);

            // Create LearningModelSession
            skillInstance.m_winmlSession = new LearningModelSession(winmlModel, GetWinMLDevice(device));

            return skillInstance;
        });
    }
    ```

3. ISkillBinding ファクトリ メソッドを実装し。

    ```csharp
    // ISkillBinding Factory method
    public IAsyncOperation<ISkillBinding> CreateSkillBindingAsync()
    {
        return AsyncInfo.Run((token) =>
        {
            var completedTask = new TaskCompletionSource<ISkillBinding>();
            completedTask.SetResult(new FaceSentimentAnalyzerBinding(SkillDescriptor, Device, m_winmlSession));
            return completedTask.Task;
        });
    }
    ```

4. 実装するようになりましたは基底インターフェイスで宣言された EvaluateAsync() メソッドを使用して、スキルのコア ロジックです。 私たちはまず、いくつかのサニティ チェックを実行しを設定する出力の特徴を取得します。

    ```csharp
    // Skill core logic
    public IAsyncAction EvaluateAsync(ISkillBinding binding)
    {
        FaceSentimentAnalyzerBinding bindingObj = binding as FaceSentimentAnalyzerBinding;
        if (bindingObj == null)
        {
            throw new ArgumentException("Invalid ISkillBinding parameter: This skill handles evaluation of FaceSentimentAnalyzerBinding instances only");
        }

        return AsyncInfo.Run(async (token) =>
        {
            // Retrieve input frame from the binding object
            VideoFrame inputFrame = (binding[FaceSentimentAnalyzerConst.SKILL_INPUTNAME_IMAGE].FeatureValue as SkillFeatureImageValue).VideoFrame;
            SoftwareBitmap softwareBitmapInput = inputFrame.SoftwareBitmap;

            // Retrieve a SoftwareBitmap to run face detection
            if (softwareBitmapInput == null)
            {
                if (inputFrame.Direct3DSurface == null)
                {
                    throw (new ArgumentNullException("An invalid input frame has been bound"));
                }
                softwareBitmapInput = await SoftwareBitmap.CreateCopyFromSurfaceAsync(inputFrame.Direct3DSurface);
            }

            // Retrieve face rectangle output feature from the binding object
            var faceRectangleFeature = binding[FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACERECTANGLE];

            // Retrieve face sentiment scores output feature from the binding object
            var faceSentimentScores = binding[FaceSentimentAnalyzerConst.SKILL_OUTPUTNAME_FACESENTIMENTSCORES];
            ...
    ```

    2 つの手順でこの特定のスキルが行われます。

    - **手順 1**:イメージに対して FaceDetector を実行し、顔の境界ボックスを取得します。

    ```csharp
            ...
            // Run face detection and retrieve face detection result
            var faceDetectionResult = await m_faceDetector.DetectFacesAsync(softwareBitmapInput);
            ...
    ```

    - **手順 2**:顔が検出された場合は、境界ボックスを調整し、使いやすくするためには、その座標を正規化 Windows.AI.MachineLearning を使用してイメージの部分の感情分析を続行します。 推定を完了すると、結果として返される各可能なセンチメント スコアを更新します。

    ```csharp
            ...
            // If a face is found, update face rectangle feature
            if (faceDetectionResult.Count > 0)
            {
                // Retrieve the face bound and enlarge it by a factor of 1.5x while also ensuring clamping to frame dimensions
                BitmapBounds faceBound = faceDetectionResult[0].FaceBox;
                var additionalOffset = faceBound.Width / 2;
                faceBound.X = Math.Max(0, faceBound.X - additionalOffset);
                faceBound.Y = Math.Max(0, faceBound.Y - additionalOffset);
                faceBound.Width = (uint)Math.Min(faceBound.Width + 2 * additionalOffset, softwareBitmapInput.PixelWidth - faceBound.X);
                faceBound.Height = (uint)Math.Min(faceBound.Height + 2 * additionalOffset, softwareBitmapInput.PixelHeight - faceBound.Y);

                // Set the face rectangle SkillFeatureValue in the skill binding object
                // note that values are in normalized coordinates between [0, 1] for ease of use
                await faceRectangleFeature.SetFeatureValueAsync(
                    new List<float>()
                    {
                            (float)faceBound.X / softwareBitmapInput.PixelWidth, // left
                            (float)faceBound.Y / softwareBitmapInput.PixelHeight, // top
                            (float)(faceBound.X + faceBound.Width) / softwareBitmapInput.PixelWidth, // right
                            (float)(faceBound.Y + faceBound.Height) / softwareBitmapInput.PixelHeight // bottom
                    });

                // Bind the WinML input frame with the adequate face bounds specified as metadata
                bindingObj.m_winmlBinding.Bind(
                    "Input3", // WinML input feature name defined in ONNX protobuf
                    inputFrame, // VideoFrame
                    new PropertySet() // VideoFrame bounds
                    {
                        { "BitmapBounds",
                            PropertyValue.CreateUInt32Array(new uint[]{ faceBound.X, faceBound.Y, faceBound.Width, faceBound.Height })
                        }
                    });

                // Run WinML evaluation
                var winMLEvaluationResult = await m_winmlSession.EvaluateAsync(bindingObj.m_winmlBinding, "");

                // Retrieve result using the WinML output feature name defined in ONNX protobuf
                var winMLModelResult = (winMLEvaluationResult.Outputs["Plus692_Output_0"] as TensorFloat).GetAsVectorView();

                // Set the SkillFeatureValue in the skill binding object related to the face sentiment scores for each possible SentimentType
                // note that we SoftMax the output of WinML to give a score normalized between [0, 1] for ease of use
                var predictionScores = SoftMax(winMLModelResult);
                await faceSentimentScores.SetFeatureValueAsync(predictionScores);
            }
            else // if no face found, reset output SkillFeatureValues with 0s
            {
                await faceRectangleFeature.SetFeatureValueAsync(FaceSentimentAnalyzerConst.ZeroFaceRectangleCoordinates);
                await faceSentimentScores.SetFeatureValueAsync(FaceSentimentAnalyzerConst.ZeroFaceSentimentScores);
            }
        });
    }
    ```

## 2. スキルを NuGet パッケージします。  <a name="CreateNuspec"></a>

すべてのまま、スキルをコンパイルして、スキルから NuGet パッケージを作成するため、アプリケーションで取り込むことができます。

([*の詳細については、ここで、NuGet パッケージは*](https://docs.microsoft.com/nuget/what-is-nuget))

NuGet パッケージを作成するには、記述する必要があります、 *.nuspec*下にあるようなファイル[Git リポジトリで元のファイルを参照してください。](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/build/Contoso.FaceSentimentAnalyzer_CS.nuspec)します。 このファイルは 2 つの主要なセクションで構成されます。

- **メタデータ**:この部分には、名前、説明、作成者と所有者、ライセンス、および依存関係が含まれています。 ここではによって異なることに注意してください、 [Microsoft.AI.Skills.SkillInterfacePreview] [ SkillInterfacePreview] NuGet パッケージ。 この NuGet パッケージはまた、ライセンスへのリンクし、インジェストの前に、承認の要求をトリガーします。

- **ファイル**:この部分は、資産、コンパイルされたビットを指します。 フレームワークのバージョン uap10.0.17763 をターゲットの場所が指していることに注意してください。 これにより、パッケージの取り込み 10.0.17763 より前のバージョンを対象とするアプリ (このスキルが必要です。 最小の OS バージョン) が受信するエラー メッセージ。

```xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="http://schemas.microsoft.com/packaging/2010/07/nuspec.xsd">
    <metadata>
        <!-- Required elements-->
        <id>Contoso.FaceSentimentAnalyzer_CS</id>
        <title>Contoso.FaceSentimentAnalyzer_CS</title>
        <version>0.0.0.5</version>
        <description>Face Sentiment Analyzer skill sample that extends the Microsoft.AI.Skills.SkillInterfacePreview APIs</description>
        <authors>Contoso</authors>
        <owners>Contoso</owners>
        <copyright>Copyright (c) Microsoft Corporation.  All rights reserved.</copyright>
        <requireLicenseAcceptance>true</requireLicenseAcceptance>
        <licenseUrl>https://github.com/Microsoft/WindowsVisionSkillsPreview/blob/master/license/doc/LICENSE_package.md</licenseUrl>
        <projectUrl>https://github.com/Microsoft/WindowsVisionSkillsPreview</projectUrl>
        <iconUrl>https://github.com/Microsoft/WindowsVisionSkillsPreview/blob/master/doc/Logo.png?raw=true</iconUrl>
        <releaseNotes>v0.0.0.5 release https://github.com/Microsoft/WindowsVisionSkillsPreview/releases</releaseNotes>
        <dependencies>
            <dependency id="Microsoft.AI.Skills.SkillInterfacePreview" version="0.5.2.12" />
        </dependencies>
        <tags>ComputerVision AI VisionSkill</tags>
    </metadata>

    <files>
        <!-- WinMD, Intellisense and resource files-->
        <file src="..\common\emotion_ferplus.onnx" target="lib\uap10.0.17763\Contoso.FaceSentimentAnalyzer" />
        <file src="..\cs\FaceSentimentAnalyzer\bin\Release\Contoso.FaceSentimentAnalyzer.winmd" target="lib\uap10.0.17763" />
        <file src="..\cs\FaceSentimentAnalyzer\bin\Release\Contoso.FaceSentimentAnalyzer.pri" target="lib\uap10.0.17763" />
        <file src="..\common\Contoso.FaceSentimentAnalyzer.xml" target="lib\uap10.0.17763" />
    </files>
</package>
```

パックする必要があります、 *.nuspec* nuget.exe を使用して ([公式サイトからダウンロード](https://www.nuget.org/downloads)) 生成するために、 *.nupkg* NuGet パッケージ ファイル。
コマンドラインを開き、移動する nuget.exe の場所を呼び出します。

```cmd
> .\nuget.exe pack <path to your .nuspec>
```

パッケージをテストするローカルにする配置して、この *.nupkg* NuGet Visual Studio でのフィードとして設定したフォルダー内のファイル ([ここに関する「方法」を参照してください。](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/README.md#PrivateNuGetFeed))。

誕生日おめでとう、作成した、最初の Windows ビジョン スキルです。 パッケージ化のスキルをアップロードする[NuGet.org](https://www.nuget.org/)!

## 3.もう一つ。 難読化して、知的財産権を非表示に資産ファイルを deobfuscating<a name="Obfuscation"></a>

改ざんしたり (モデル ファイル、画像など)、スキル資産へのアクセス、コンシューマーを阻止するには、ビルド前の手順としてファイルを難読化し、実行時にファイルを deobfuscate できます。 [の例では、GitHub サンプル](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/FaceSentimentAnalyzer)を利用するヘルパー クラスの実装が含まれて[Windows.Security.Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography)に[難読化](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Obfuscator)コンパイル時にファイルと[deobfuscate](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Deobfuscator)実行時にします。 この部分でのみ表示される注記をC++/WinRT バージョンを保持する例のスキルのC#バージョンに簡単です。  

- 難読化ことは、1 回実行するか、すべての時間を実行するプロジェクトを設定し、資産として出力を直接使用するビルド前イベントとは。 この例では、専用のコンパイル ツール (Obfuscator.exe) を使用します。 スキル、コンパイル時のビルド前イベントとして起動する前に、このツールのコンパイルが最初になっていることを確認するがあります。 コンパイル時に、開発用コンピューターで実行をするためコンパイルできる任意のターゲットとサポートされるプラットフォームを使用するとそれに注意してください (つまりこの場合*デバッグ/Win32*)。

    Visual studio では、このビルド前イベントを設定できます。

- C++プロジェクト:***スキル プロジェクトを右クリックして***]-> [uncollapse***ビルド イベント***選択]-> [***ビルド前イベント***]-> [入力、***コマンドライン***
- C#プロジェクト:***スキル プロジェクトを右クリックして***選択]-> [***ビルド イベント***]-> [入力、***ビルド前に実行するコマンドライン***

    このコマンドでは:
- まず、資産ファイルをローカルにコピーします。
- それを暗号化する *.crypt* (任意の拡張機能名を指定できます) ファイルで定義されている GUID キーが必要なロジックを使用して
- ローカル ファイルを削除します。

    ** **スキルを一意にするサンプルで提案されている暗号化ロジックを変更するをお勧めことに注意してください。** **

    ```cmd
    copy $(ProjectDir)..\..\Common\emotion_ferplus.onnx $(ProjectDir) &amp;&amp; ^$(ProjectDir)..\Obfuscator\Win32\Debug\Obfuscator.exe $(ProjectDir)emotion_ferplus.onnx $(ProjectDir) emotion_ferplus.crypt 678BD455-4190-45D3-B5DA-41543283C092 &amp;&amp; ^del $(ProjectDir)emotion_ferplus.onnx
    ```

- Deobfuscation は単純なヘルパー スキルによって取り込まれた Windows ランタイム コンポーネントを使用して公開されます。 復号化ロジックでは、暗号化前の手順で定義されているいずれかに従います。

    ```cpp
    // FaceSentimentAnalyzerSkill.cpp
    ...
    #include "winrt/DeobfuscationHelper.h"
    ...

    // ISkill Factory method
    Windows::Foundation::IAsyncOperation<winrt::Contoso::FaceSentimentAnalyzer::FaceSentimentAnalyzerSkill> FaceSentimentAnalyzerSkill::CreateAsync(
        ISkillDescriptor descriptor,
        ISkillExecutionDevice device)
    {
        ...

        // Load WinML model
        auto modelFile = Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri(L"ms-appx:///Contoso.FaceSentimentAnalyzer/" + WINML_MODEL_FILENAME)).get();

        // Deobfuscate model file and retrieve LearningModel instance
        LearningModel learningModel = winrt::DeobfuscationHelper::Deobfuscator::DeobfuscateModelAsync(modelFile, descriptor.Id()).get();

        ...

    ```

[!INCLUDE [help](../includes/get-help-vision.md)]

[SkillInterfacePreview]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview

[ISkillDescriptor]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor

[ISkill]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill

[ISkillBinding]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding

[VisionSkillBindingHelper]: https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.visionskillbindinghelper
