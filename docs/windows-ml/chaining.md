---
author: rosanevallim
title: チェーン内で複数の ML モデルを実行する
description: このチュートリアルでは、最適な GPU パフォーマンスで、複数の機械学習モデルを連続して実行する方法について説明します
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 4fd0c47a04b96922bf9ea6f498d54d827c5f257d
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "66180834"
---
# <a name="executing-multiple-ml-models-in-a-chain"></a>チェーン内で複数の ML モデルを実行する

Windows ML では、GPU パスを慎重に最適化することで、モデル チェーンの高パフォーマンスの読み込みと実行がサポートされます。 モデル チェーンは、連続して実行される 2 つ以上のモデルによって定義され、あるモデルの出力が、チェーン内の次のモデルへの入力となります。 

Windows ML でモデルの効率的なチェーンを作成する方法を説明するために、おもちゃの例として FNS-Candy スタイル転送の ONNX モデルを使用してみましょう。 この種類のモデルについては、[GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer)の FNS-Candy スタイル転送のサンプル フォルダーを参照してください。

たとえば、同じ FNS-Candy モデル (**mosaic.onnx**) の 2 つのインスタンスで構成されるチェーンを実行するとします。 アプリケーション コードは、チェーン内の最初のモデルにイメージを渡し、出力を計算してから、変換されたイメージを FNS-Candy の別のインスタンスに渡して最終的なイメージを生成します。  

次の手順では、Windows ML を使用してこれを実現する方法を説明します。

>[!Note]
>実際のシナリオでは、2 つの異なるモデルを使用することがほとんどですが、概念を説明するにはこれで十分です。

1. まず、**mosaic.onnx** モデルを読み込んで、使用できるようにします。
  ```cpp
  std::wstring filePath = L"path\\to\\mosaic.onnx"; 
  LearningModel model = LearningModel::LoadFromFilePath(filePath);
  ```

  ```cs
  string filePath = "path\\to\\mosaic.onnx";
  LearningModel model = LearningModel.LoadFromFilePath(filePath);
  ```

2. 次に、入力パラメーターと同じモデルを使用して、デバイスの既定の GPU に同一の 2 つのセッションを作成します。 
  ```cpp
  LearningModelSession session1(model, LearningModelDevice(LearningModelDeviceKind::DirectX));
  LearningModelSession session2(model, LearningModelDevice(LearningModelDeviceKind::DirectX));
  ```

  ```cs
  LearningModelSession session1 = 
    new LearningModelSession(model, new LearningModelDevice(LearningModelDeviceKind.DirectX));
  LearningModelSession session2 = 
    new LearningModelSession(model, new LearningModelDevice(LearningModelDeviceKind.DirectX));
  ```

> [!NOTE]
>チェーンによるパフォーマンス上の利点を得るためには、すべてのモデルに対して同一の GPU セッションを作成する必要があります。 そうしないと、GPU から CPU への追加のデータ移動が発生し、パフォーマンスが低下する可能性があります。

3. 次のコード行によって、各セッションのバインドが作成されます。
  ```cpp
  LearningModelBinding binding1(session1);
  LearningModelBinding binding2(session2);
  ```

  ```cs
  LearningModelBinding binding1 = new LearningModelBinding(session1);
  LearningModelBinding binding2 = new LearningModelBinding(session2);
  ```

4. 次に、最初のモデル用の入力をバインドします。 モデルと同じパスに配置されているイメージを渡します。 この例で、イメージの名前は "fish_720.png" です。
  ```cpp
  //get the input descriptor
  ILearningModelFeatureDescriptor input = model.InputFeatures().GetAt(0);
  //load a SoftwareBitmap
  hstring imagePath = L"path\\to\\fish_720.png";

  // Get the image and bind it to the model's input
  try
  {
    StorageFile file = StorageFile::GetFileFromPathAsync(imagePath).get();
    IRandomAccessStream stream = file.OpenAsync(FileAccessMode::Read).get();
    BitmapDecoder decoder = BitmapDecoder::CreateAsync(stream).get();
    SoftwareBitmap softwareBitmap = decoder.GetSoftwareBitmapAsync().get();
    VideoFrame videoFrame = VideoFrame::CreateWithSoftwareBitmap(softwareBitmap);
    ImageFeatureValue image = ImageFeatureValue::CreateFromVideoFrame(videoFrame);
    binding1.Bind(input.Name(), image);
  }
  catch (...)
  {
    printf("Failed to load/bind image\n");
  }
  ```

  ```cs
  //get the input descriptor
  ILearningModelFeatureDescriptor input = model.InputFeatures[0];
  //load a SoftwareBitmap
  string imagePath = "path\\to\\fish_720.png";

  // Get the image and bind it to the model's input
  try
  {
      StorageFile file = await StorageFile.GetFileFromPathAsync(imagePath);
      IRandomAccessStream stream = await file.OpenAsync(FileAccessMode.Read);
      BitmapDecoder decoder = await BitmapDecoder.CreateAsync(stream);
      SoftwareBitmap softwareBitmap = await decoder.GetSoftwareBitmapAsync();
      VideoFrame videoFrame = VideoFrame.CreateWithSoftwareBitmap(softwareBitmap);
      ImageFeatureValue image = ImageFeatureValue.CreateFromVideoFrame(videoFrame);
      binding1.Bind(input.Name, image);
  }
  catch
  {
      Console.WriteLine("Failed to load/bind image");
  }
  ```

5. 最初のモデルの評価の出力をチェーン内の次のモデルで使用するには、チェーンのマーカーを設定するために、空の出力テンソルを作成してその出力をバインドする必要があります。
  ```cpp
  //get the output descriptor
  ILearningModelFeatureDescriptor output = model.OutputFeatures().GetAt(0);
  //create an empty output tensor 
  std::vector<int64_t> shape = {1, 3, 720, 720};
  TensorFloat outputValue = TensorFloat::Create(shape); 
  //bind the (empty) output
  binding1.Bind(output.Name(), outputValue);
  ```

  ```cs
  //get the output descriptor
  ILearningModelFeatureDescriptor output = model.OutputFeatures[0];
  //create an empty output tensor 
  List<long> shape = new List<long> { 1, 3, 720, 720 };
  TensorFloat outputValue = TensorFloat.Create(shape);
  //bind the (empty) output
  binding1.Bind(output.Name, outputValue);
  ```

> [!NOTE]
>出力をバインドするときには、**TensorFloat** データ型を使用する必要があります。 これにより、最初のモデルの評価完了後にテンソル化が解除されるのを防ぐことができ、結果的に 2 番目のモデルの読み込みとバインドの操作のための余分な GPU キューが生成されるのも回避されます。

6. ここで、最初のモデルの評価を実行し、その出力を次のモデルの入力にバインドします。
  ```cpp
  //run session1 evaluation
  session1.EvaluateAsync(binding1, L"");
  //bind the output to the next model input
  binding2.Bind(input.Name(), outputValue);
  //run session2 evaluation
  auto session2AsyncOp = session2.EvaluateAsync(binding2, L"");
  ```

  ```cs
  //run session1 evaluation
  await session1.EvaluateAsync(binding1, "");
  //bind the output to the next model input
  binding2.Bind(input.Name, outputValue);
  //run session2 evaluation
  LearningModelEvaluationResult results = await session2.EvaluateAsync(binding2, "");
  ```

7. 最後に、次のコード行を使用して、両方のモデルを実行した後に生成される最終的な出力を取得してみましょう。
  ```cpp
  auto finalOutput = session2AsyncOp.get().Outputs().First().Current().Value();
  ```

  ```cs
  var finalOutput = results.Outputs.First().Value;
  ```

以上で作業は終了です。 使用可能な GPU リソースを最大限に活用することで、両方のモデルを連続して実行できるようになりました。 

[!INCLUDE [help](../includes/get-help.md)]
