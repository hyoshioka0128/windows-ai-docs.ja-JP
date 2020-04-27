---
title: 独自のビジョン スキルを作成する (C#/C++)
description: このチュートリアルでは、独自の Windows Vision Skills を作成する方法について説明します。
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: windows 10, windows ai, windows vision skills
ms.localizationpriority: medium
ms.openlocfilehash: 0b61a7261b04d8e01a3ca8ce5e9acd8a770f1cdf
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156218"
---
# <a name="tutorial-create-your-own-windows-vision-skill-c"></a>チュートリアル: 独自の Windows Vision Skills を作成する (C#)

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

カスタム ビジョン ソリューションがすでに存在する場合、このチュートリアルは、[Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] ベースの API を拡張することによってそのソリューションを Windows Vision Skills 内にラップする方法を示します。

では、次のものを活用する顔の感情アナライザー スキルを構築します。

- [Windows.Media.FaceAnalysis](https://docs.microsoft.com/uwp/api/windows.media.faceanalysis) および [Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) API
- 顔の画像から感情を推測する ONNX 形式の機械学習モデル

このスキルでは、以下を取得します。

- 入力画像

そして、以下を出力します。

- 評価する各感情に関する [0,1] の範囲にある単精度スコア値のテンソル
- 顔のバウンディングボックスの相対座標を定義する [0,1] の範囲にある浮動小数値のテンソル: 左 (x,y)、上 (x,y)、右 (x,y)、および下 (x,y)

![FaceSentimentAnalysis スキルの入力および出力例の図](../images/vision-skills-FaceSentimentAnalysis.png)

この例の C# および C++/WinRT バージョンの完全なソース コードは、次のサンプル GitHub リポジトリで入手できます。

- [C# のスキルの例](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs)
- [C++/WinRT のスキルの例](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp)

このチュートリアルでは、次のことについて説明します。

1. Windows Vision Skills に必要な[主要なインターフェイスの実装](#CreateMainClasses)
2. NuGet パッケージを生成するための [.nuspec の作成](#CreateNuspec)
3. ファイルの内容を隠すための[難読化および難読化解除](#Obfuscation)の各ファイル

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (または Visual Studio 2017 バージョン 15.7.4 以降)
- Windows 10 バージョン 1809 以降
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) バージョン 1809 以降
- [Microsoft.AI.Skills.SkillInterfacePreview NuGet パッケージ](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/)

## <a name="1-create-and-implement-the-main-skill-classes"></a>1.主要なスキル クラスを作成して実装する <a name="CreateMainClasses"></a>

まず、次の主要なスキル クラスを実装する必要があります (詳細については、「[API の重要な概念](important-api-concepts.md)」を参照)。

- [ISkillDescriptor](#ISkillDescriptor)
- [ISkillBinding](#ISkillBinding)
- [ISkill](#ISkill)

Visual Studio でカスタム ビジョン ソリューションを開きます。

### <a name="a-iskilldescriptor"></a>a。 ISkillDescriptor <a name="ISkillDescriptor"></a>

スキルに関する情報や、サポートされる実行デバイス (CPU や GPU など) の一覧を提供し、スキルのファクトリ オブジェクトとして機能する、[ISkillDescriptor][ISkillDescriptor] から継承されたスキル記述子クラスを作成して実装します。

1. [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] 名前空間をインポートし、[ISkillDescriptor][ISkillDescriptor] インターフェイスからクラスを派生させます。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerDescriptor : ISkillDescriptor
    {
        ...
    }
    ```

2. スキルに必要な入力と出力の説明を保持する 2 つのメンバー変数を作成します。 次に、記述子のコンストラクターで、入力および出力特徴の記述子に応じてそれらの変数に入力します。 さらに、スキルの必要なすべての説明プロパティを提供する *SkillInformation* オブジェクトを作成します。

    ```csharp
    ...
    // Member variables to hold input and output descriptions
    private List<ISkillFeatureDescriptor> m_inputSkillDesc;
    private List<ISkillFeatureDescriptor> m_outputSkillDesc;

    // Properties required by the interface
    public IReadOnlyList<ISkillFeatureDescriptor> InputFeatureDescriptors => m_inputSkillDesc;
    public IReadOnlyDictionary<string, string> Metadata => null;
    public IReadOnlyList<ISkillFeatureDescriptor> OutputFeatureDescriptors => m_outputSkillDesc;

    // Constructor
    public FaceSentimentAnalyzerDescriptor()
    {
        Information = SkillInformation.Create(
                "FaceSentimentAnalyzer", // Name
                "Finds a face in the image and infers its predominant sentiment from a set of 8 possible labels", // Description
                new Guid(0xf8d275ce, 0xc244, 0x4e71, 0x8a, 0x39, 0x57, 0x33, 0x5d, 0x29, 0x13, 0x88), // Id
                new Windows.ApplicationModel.PackageVersion() { Major = 0, Minor = 0, Build = 0, Revision = 8 }, // Version
                "Contoso Developer", // Author
                "Contoso Publishing" // Publisher
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

3. スキルを実行するための利用可能なサポートされる実行デバイスを探し、それをコンシューマーに返す必要なメソッドを実装します。 ここでは、D3D バージョン 12 以降をサポートしている CPU およびすべての DirectX デバイスを返します。

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

4. スキルをインスタンス化するために必要なメソッドを実装します。

    - どちらかのメソッドで、最適な利用可能デバイスを選択します。

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

    - もう一方で、指定された実行デバイスを使用します。

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

### <a name="b-iskillbinding"></a>b. **ISkillBinding** <a name="ISkillBinding"></a>

スキルによって使用および生成される入力および出力変数を含む、[ISkillBinding][ISkillBinding] インターフェイスから継承されたスキル バインド クラスを作成して実装します。

1. [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] 名前空間をインポートし、[ISkillBinding][ISkillBinding] インターフェイスとその必要なコレクション型からクラスを派生させます。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerBinding : IReadOnlyDictionary<string, ISkillFeature>, ISkillBinding
    {
        ...

    ```

2. 最初に、次の 2 つのメンバー変数を作成します。

    - 1 つは、"InputImage" という名前の入力画像の特徴を保持するために基本インターフェイスで提供されるヘルパー クラス [VisionSkillBindingHelper][VisionSkillBindingHelper] です。

    ```csharp
    private VisionSkillBindingHelper m_bindingHelper = null;
    ```

    - もう一方は、後でスキル クラスでコンストラクターへの引数として指定される LearningModelSession に渡すために使用される LearningModelBinding を保持します。

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

    次に、コンストラクターを実装します。 コンストラクターが *internal* であることに注意してください。このパラダイムでは、ISkillBinding インスタンスはスキルによって作成されるため、スタンドアロン コンストラクターを公開すべきではありません。

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

3. スキルによって出力される感情の種類の読み取りを容易にする列挙型を作成します。

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

4. バインドの取得および設定操作を容易にするオプションの追加メソッドを実装します。

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

### <a name="c-iskill"></a>c. **ISkill** <a name="ISkill"></a>

スキル ロジックを実行し、指定された一連の入力から出力を生成する、[ISkill][ISkill] インターフェイスから継承されたスキル クラスを作成して実装します。 また、これは ISkillBinding 派生クラスのファクトリ オブジェクトとしても機能します。

1. [Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] 名前空間をインポートし、[ISkill][ISkill] インターフェイスからクラスを派生させます。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerSkill : ISkill
    {
        ...
    ```

2. 最初に、次の 2 つのメンバー変数を作成します。

    - 1 つは、入力画像の顔を見つける FaceDetector を保持するためのものです。

    ```csharp
    private FaceDetector m_faceDetector = null;
    ```

    - もう 1 つは、感情分析モデルを評価するために使用される LearningModelSession を保持するためのものです。

    ```csharp
    private LearningModelSession m_winmlSession = null;
    ```

    必要なプロパティを宣言します。

    ```csharp
    public ISkillDescriptor SkillDescriptor { get; private set; }
    public ISkillExecutionDevice Device { get; private set; }
    ```

    次に、コンストラクターと静的ファクトリ メソッドを実装します。 コンストラクターが *private* であり、ファクトリ メソッドが *internal* であることに注意してください。このパラダイムでは、ISkill インスタンスはスキル記述子によって作成されるため、スタンドアロン コンストラクターを公開すべきではありません。

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

3. 次に、ISkillBinding ファクトリ メソッドを実装します。

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

4. この段階で、まだ実装されていないものは、基本インターフェイスで宣言されている EvaluateAsync() メソッドを経由したスキルのコア ロジックだけです。 まず、何らかのサニティ チェックを実行し、設定するための出力特徴を取得します。

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

    その後、この特定のスキルは次の 2 つの手順で処理を続行します。

    - **手順 1**:画像に対して FaceDetector を実行し、顔のバウンディングボックスを取得します。

    ```csharp
            ...
            // Run face detection and retrieve face detection result
            var faceDetectionResult = await m_faceDetector.DetectFacesAsync(softwareBitmapInput);
            ...
    ```

    - **手順 2**: 顔が検出された場合は、バウンディングボックスを調整し、その座標を使いやすいように正規化した後、Windows.AI.MachineLearning を使用して画像のその部分の感情分析を続行します。 推論が完了したら、結果として返される可能性のある各感情のスコアを更新します。

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

## <a name="2-package-your-skill-to-nuget"></a>2.スキルを NuGet にパッケージ化する <a name="CreateNuspec"></a>

後は、スキルをコンパイルし、そのスキルから NuGet パッケージを作成してアプリケーションが取り込めるようにするだけです。

([*NuGet パッケージの詳細については、ここを参照*](https://docs.microsoft.com/nuget/what-is-nuget))

NuGet パッケージを作成するには、次のような *.nuspec* ファイルを作成する必要があります ([Git リポジトリの元のファイルを参照](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/build/Contoso.FaceSentimentAnalyzer_CS.nuspec))。 このファイルは、次の 2 つの主なセクションで構成されています。

- **metadata**: この部分には、名前、説明、作成者と所有者、ライセンス、および依存関係が含まれています。 ここでは、[Microsoft.AI.Skills.SkillInterfacePreview][SkillInterfacePreview] NuGet パッケージに依存していることに注意してください。 この NuGet パッケージはライセンスにもリンクしており、取り込みの前に承認のための要求をトリガーします。

- **files**: この部分では、コンパイルされたビットと資産を指しています。 ターゲットの場所がフレームワーク バージョン uap10.0.17763 を指していることに注意してください。 これにより、10.0.17763 (このスキルが必要とする最小の OS バージョン) より前のバージョンを対象とするパッケージを取り込むアプリが、確実にエラー メッセージを受信します。

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

次に、nuget.exe ([公式サイトからのダウンロード](https://www.nuget.org/downloads)) を使用して *.nuspec* をパッケージングして *.nupkg* NuGet パッケージ ファイルを生成する必要があります。
コマンド ラインを開き、nuget.exe の場所に移動して、次のように呼び出します。

```cmd
> .\nuget.exe pack <path to your .nuspec>
```

パッケージをローカルでテストするには、この *.nupkg* ファイルを Visual Studio で NuGet フィードとして設定したフォルダーに置くことができます ([その方法については、ここを参照](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/README.md#PrivateNuGetFeed))。

これで、最初の Windows Vision Skills が作成されました。 パッケージ化されたスキルを [NuGet.org](https://www.nuget.org/) にアップロードできます。

## <a name="3-one-more-thing-obfuscating-and-deobfuscating-asset-files-to-conceal-your-intellectual-property"></a>3.もう 1 つの点ですが... 知的財産を隠すための資産ファイルの難読化および難読化解除<a name="Obfuscation"></a>

コンシューマーによるスキル資産 (モデル ファイルや画像など) の改ざんまたはアクセスを防止するために、ビルド前の手順としてファイルを難読化し、実行時にファイルを難読化解除することができます。 この[サンプル GitHub の例](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/FaceSentimentAnalyzer)には、コンパイル時にファイルを[難読化](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Obfuscator)し、実行時に[難読化解除](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Deobfuscator)するために [Windows.Security.Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography) を活用するヘルパー クラスの実装が含まれています。 C# バージョンの単純さを維持するために、この部分では、スキルの例の C++/WinRT バージョンでのみ示されていることに注意してください。  

- 難読化は、プロジェクトで常に実行するか、または 1 回実行し、その出力を資産として直接使用するように設定できるビルド前のイベントです。 この例では、専用のコンパイルされたツール (Obfuscator.exe) を使用します。 このツールは、スキル コンパイル時のビルド前のイベントとして呼び出す前に、最初にコンパイルしておく必要があります。 コンパイル時には開発用コンピューターで実行されるため、サポートされる任意のターゲットおよびプラットフォーム (この場合は、*Debug/Win32*) を使用して 1 度コンパイルできることに注意してください。

    このビルド前のイベントは、Visual Studio で次のように設定できます。

- C++ プロジェクト: **スキル プロジェクトを右クリックする** -> **[Build Event] (ビルド イベント)** を展開する -> **[ビルド前のイベント]** を選択する  -> **[コマンド ライン]** を入力する
- C# プロジェクト: **スキル プロジェクトを右クリックする** -> **[Build Event] (イベントのビルド)** を選択する -> **[ビルド前に実行するコマンド ライン]** を入力する

    このコマンドは、1:資産ファイルをローカルでコピーし、2: GUID キーを必要とする定義済みのロジックを使用して、そのファイルを *.crypt* ファイル (希望する任意の拡張機能名にすることができます) に暗号化した後、3: ローカル ファイルを削除します。

> [!NOTE]
> サンプルで提案されている暗号化ロジックを、実際のスキルに固有のロジックに変更することをお勧めします。

    ```cmd
    copy $(ProjectDir)..\..\Common\emotion_ferplus.onnx $(ProjectDir) &amp;&amp; ^$(ProjectDir)..\Obfuscator\Win32\Debug\Obfuscator.exe $(ProjectDir)emotion_ferplus.onnx $(ProjectDir) emotion_ferplus.crypt 678BD455-4190-45D3-B5DA-41543283C092 &amp;&amp; ^del $(ProjectDir)emotion_ferplus.onnx
    ```

- 難読化解除は、スキルによって取り込まれる単純なヘルパー Windows ランタイム コンポーネント経由で公開されます。 その暗号化解除ロジックは、前の手順で定義されている暗号化ロジックに従います。

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
