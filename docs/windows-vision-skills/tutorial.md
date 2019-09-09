---
title: 独自のビジョンスキルを作成C#するC++(/)
description: このチュートリアルを使用して、独自の Windows ビジョンスキルを作成する方法について説明します。
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: windows 10、windows ai、windows ビジョンのスキル
ms.localizationpriority: medium
ms.openlocfilehash: 0b61a7261b04d8e01a3ca8ce5e9acd8a770f1cdf
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156218"
---
# <a name="tutorial-create-your-own-windows-vision-skill-c"></a>チュートリアル:独自の Windows ビジョンスキルを作成C#する ()

> [!NOTE]
> 一部の情報はプレリリース版の製品に関連していますが、製品版のリリース前に大幅に変更されている可能性があります。 Microsoft は、ここで提供される情報に関して、明示または黙示を問わず、いかなる保証も行いません。

カスタムビジョンソリューションが既にある場合、このチュートリアルでは、 [SkillInterfacePreview][SkillInterfacePreview] base API を拡張して、ソリューションを Windows ビジョンのスキルでラップする方法を示します。

次のものを活用する face センチメント analyzer のスキルを構築してみましょう。

- [FaceAnalysis](https://docs.microsoft.com/uwp/api/windows.media.faceanalysis) Api と[Windows. AI e ラーニング](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)api
- 顔イメージからセンチメントを推測する、ONNX 形式の機械学習モデル

このスキルには次のものが必要です。

- 入力イメージ

次のように出力されます。

- 評価される各センチメントの範囲 [0, 1] の1つの精度スコア値
- [0, 1] の範囲に含まれる float 値のうち、面の境界ボックスの相対座標: 左 (x、y)、上 (x、y)、右 (x、y)、下 (x、y) を定義します。

![FaceSentimentAnalysis のスキルの入力と出力の例の図](../images/vision-skills-FaceSentimentAnalysis.png)

この例のC#およびC++/WinRT バージョンの完全なソースコードは、サンプル GitHub リポジトリで入手できます。

- [C#スキルの例](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cs)
- [C++/WinRT のスキルの例](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp)

このチュートリアルでは、次の手順について説明します。

1. Windows ビジョンのスキルに必要な[主なインターフェイスの実装](#CreateMainClasses)
2. NuGet パッケージを生成するため[の. nuspec の作成](#CreateNuspec)
3. ファイルの難読化と難読化を解除[して](#Obfuscation)、コンテンツを隠す

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)(または Visual Studio 2017、バージョン15.7.4 以降)
- Windows 10 バージョン 1809 以降
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)バージョン1809以降
- [SkillInterfacePreview NuGet パッケージ](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/)の場合は、

## 1. 主要なスキルクラスを作成して実装する<a name="CreateMainClasses"></a>

最初に、主要なスキルクラスを実装する必要があります (詳細については、「 [API の重要な概念](important-api-concepts.md)」を参照してください)。

- [Isの記述子](#ISkillDescriptor)
- [Isのバインド](#ISkillBinding)
- [ISkill](#ISkill)

Visual Studio でカスタムビジョンソリューションを開きます。

### a. Isの記述子<a name="ISkillDescriptor"></a>

スキルに関する情報を提供する[isの記述子][ISkillDescriptor]から継承されたスキル記述子クラスを作成して実装し、サポートされる実行デバイス (CPU、GPU など) の一覧を提供し、そのスキルのファクトリオブジェクトとして機能します。

1. [SkillInterfacePreview][SkillInterfacePreview]名前空間をインポートし、 [is descriptor][ISkillDescriptor]インターフェイスからクラスを派生させます。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerDescriptor : ISkillDescriptor
    {
        ...
    }
    ```

2. スキルに必要な入力と出力の説明を保持する2つのメンバー変数を作成します。 次に、記述子のコンストラクターで、入力と出力の機能記述子を使用してそれを入力します。 また、スキルの必要な説明プロパティをすべて提供する*Skillinformation*オブジェクトを作成します。

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

3. 使用可能なサポートされている実行デバイスを検索する必須メソッドを実装して、スキルを実行してコンシューマーに返します。 この例では、D3D バージョン12以降をサポートする CPU とすべての DirectX デバイスを返します。

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

    - 次のいずれかの方法で、最適なデバイスを選択します。

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

    - もう1つは、指定された実行デバイスを使用します。

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

### b. **Isのバインド**<a name="ISkillBinding"></a>

使用され、スキルによって生成される入力変数と出力変数を格納する、 [isて binding][ISkillBinding]インターフェイスから継承されたスキルバインドクラスを作成して実装します。

1. [SkillInterfacePreview][SkillInterfacePreview]名前空間をインポートし、 [is binding][ISkillBinding]インターフェイスおよび必要なコレクション型からクラスを派生させます。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerBinding : IReadOnlyDictionary<string, ISkillFeature>, ISkillBinding
    {
        ...

    ```

2. 最初に2つのメンバー変数を作成します。

    - 1つは、"InputImage" という名前の入力イメージ機能を保持するために、基本インターフェイスに用意されているヘルパークラス[VisionSkillBindingHelper][VisionSkillBindingHelper]です。

    ```csharp
    private VisionSkillBindingHelper m_bindingHelper = null;
    ```

    - もう1つは、スキルクラスの後半で、コンストラクターの引数として指定された LearningModelSession に渡すために使用される LearningModelBinding を保持します。

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

    とは、コンストラクターを実装します。 コンストラクターは*内部*にあることに注意してください。このパラダイムでは、Isare Binding インスタンスはスキルによって作成されるため、スタンドアロンコンストラクターを公開することはできません。

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

3. スキルによって出力されるセンチメント型の読み取りを容易にする列挙型を作成する

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

4. バインドに対する get 操作と set 操作を容易にするオプションの追加メソッドを実装する

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

### c. **Iskill**<a name="ISkill"></a>

[Iskill][ISkill]インターフェイスから継承されたスキルクラスを作成して実装します。このクラスは、スキルロジックを実行し、入力のセットを指定して出力を生成します。 また、ISkillBinding 派生元のファクトリオブジェクトとしても機能します。

1. [SkillInterfacePreview][SkillInterfacePreview]名前空間をインポートし、 [iskill][ISkill]インターフェイスからクラスを派生させます。

    ```csharp
    ...
    using Microsoft.AI.Skills.SkillInterfacePreview;
    ...

    public sealed class FaceSentimentAnalyzerSkill : ISkill
    {
        ...
    ```

2. 最初に2つのメンバー変数を作成します。

    - 1つは、FaceDetector を保持して入力イメージ上の顔を検索するためのものです。

    ```csharp
    private FaceDetector m_faceDetector = null;
    ```

    - もう1つは、センチメント分析モデルの評価に使用される LearningModelSession を保持するためのものです。

    ```csharp
    private LearningModelSession m_winmlSession = null;
    ```

    必要なプロパティを宣言します。

    ```csharp
    public ISkillDescriptor SkillDescriptor { get; private set; }
    public ISkillExecutionDevice Device { get; private set; }
    ```

    とは、コンストラクターと静的ファクトリメソッドを実装します。 コンストラクターが*プライベート*で、ファクトリメソッドが*内部*にあることに注意してください。このパラダイムでは、ISkill インスタンスはスキル記述子によって作成されるため、スタンドアロンコンストラクターを公開することはできません。

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

3. 次に、Isをバインドするファクトリメソッドを実装します。

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

4. 現在実装されているものは、基本インターフェイスで宣言された EvaluateAsync () メソッドを使用したスキルの核となるロジックです。 まず、いくつかの正常性チェックを行い、設定する出力機能を取得します。

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

    この特定のスキルは、次の2つの手順で進行します。

    - **手順 1**:画像に対して FaceDetector を実行し、顔の境界ボックスを取得します。

    ```csharp
            ...
            // Run face detection and retrieve face detection result
            var faceDetectionResult = await m_faceDetector.DetectFacesAsync(softwareBitmapInput);
            ...
    ```

    - **手順 2**:顔が検出された場合は、境界ボックスを調整し、使いやすさのためにその座標を正規化し、センチメントを使用してイメージのその部分の分析を続行します。 推論が完了したら、結果として返される可能性がある各センチメントのスコアを更新します。

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

## 2. スキルを NuGet にパッケージ化する<a name="CreateNuspec"></a>

残りのことは、スキルをコンパイルしてスキルから NuGet パッケージを作成し、アプリケーションがそれを取り込むことができるようにすることです。

([*NuGet パッケージの詳細についてはこちらを参照してください*](https://docs.microsoft.com/nuget/what-is-nuget))

NuGet パッケージを作成するには、次のような*nuspec*ファイルを[Git リポジトリの元のファイル](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/SentimentAnalyzerCustomSkill/build/Contoso.FaceSentimentAnalyzer_CS.nuspec)に書き込む必要があります。 このファイルは、次の2つの主要なセクションで構成されています。

- **メタデータ**:この部分には、名前、説明、作成者と所有者、ライセンス、および依存関係が含まれています。 この例では、 [SkillInterfacePreview][SkillInterfacePreview] NuGet パッケージに依存していることに注意してください。 また、この NuGet パッケージはライセンスにリンクし、インジェスト前に承認要求をトリガーします。

- **ファイル**:この部分は、コンパイル済みのビットと資産を指します。 ターゲットの場所は、フレームワークのバージョン uap 10.0.17763 を指していることに注意してください。 これにより、アプリは10.0.17763 よりも前のバージョンを対象とするパッケージを取り込みすることができます (このスキルに必要な最小 OS バージョンでは、エラーメッセージが表示されます)。

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

次に、nuget.exe ([公式サイトからダウンロード](https://www.nuget.org/downloads)) を使用して*nuspec*をパックして、 *nupkg* nuget パッケージファイルを生成する必要があります。
コマンドラインを開き、nuget.exe の場所に移動して、次のように呼び出します。

```cmd
> .\nuget.exe pack <path to your .nuspec>
```

パッケージをローカルでテストするには、Visual Studio で NuGet フィードとして設定したフォルダーにこの*nupkg*ファイルを配置します ([詳細については、こちらを参照してください](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/README.md#PrivateNuGetFeed))。

バンザイは、初めての Windows ビジョンスキルを作成しました。 パッケージ化されたスキルを[NuGet.org](https://www.nuget.org/)にアップロードできます。

## 3.もう一つ。 資産ファイルを難読化および難読化して、知的財産を隠す<a name="Obfuscation"></a>

コンシューマーがスキルアセット (モデルファイル、イメージなど) の改ざんやアクセスを防ぐためには、ファイルをビルド前の手順として難読化し、実行時に deobfuscate 化することができます。 この[サンプル GitHub の例で](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/FaceSentimentAnalyzer)は、コンパイル時にファイルを[難読](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Obfuscator)化[し、実行時に難読化](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill/cpp/Skill/Deobfuscator)するヘルパークラスの[実装につい](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography)て説明します。 この部分は、 C++ C#バージョンをより単純にするために、例として使用されているスキルの/WinRT バージョンでのみ表示されることに注意してください。  

- 難読化とは、プロジェクトを常に実行するように設定することも、1回だけ実行して出力を資産として直接使用することもできる、ビルド前のイベントです。 この例では、専用のコンパイル済みツール (ngen.exe) を使用します。 このツールを最初にコンパイルしてから、スキルコンパイル時間のビルド前イベントとして呼び出す必要があります。 コンパイル時には開発用コンピューターで実行されるため、サポートされている任意のターゲットとプラットフォーム (この場合は*Debug/Win32*) を使用してコンパイルすることができます。

    Visual Studio でこのビルド前イベントを設定するには、次のようにします。

- C++プロジェクト:**スキルプロジェクトを右クリック**し、 **[ビルドイベント]** の折りたたみ を > > **[ビルド前のイベント]** を選択し、**コマンドライン**を入力 >
- C#プロジェクト:**スキルプロジェクトを右クリックして**>**ビルドイベント**の選択-**ビルド前イベントのコマンドライン**を入力 >

    次のコマンドを実行します。1:アセットファイルをローカルにコピーします 2:は、GUID キー3を必要とするで定義されているロジックを使用して、ファイルを暗号化ファイル (任意の拡張子名にすることができます) に暗号化し*ます*。ローカルファイルを削除します。

> [!NOTE]
> このサンプルで提案されている暗号化ロジックを変更して、スキルに固有のものにすることをお勧めします。

    ```cmd
    copy $(ProjectDir)..\..\Common\emotion_ferplus.onnx $(ProjectDir) &amp;&amp; ^$(ProjectDir)..\Obfuscator\Win32\Debug\Obfuscator.exe $(ProjectDir)emotion_ferplus.onnx $(ProjectDir) emotion_ferplus.crypt 678BD455-4190-45D3-B5DA-41543283C092 &amp;&amp; ^del $(ProjectDir)emotion_ferplus.onnx
    ```

- 非難読化は、スキルによって取り込まれたする単純なヘルパー Windows ランタイムコンポーネントによって公開されています。 復号化ロジックは、前の手順で定義した暗号化に従います。

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
