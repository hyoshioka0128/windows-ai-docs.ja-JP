---
author: rosanevallim
title: チェーンの複数の ML モデルを実行します。
description: このチュートリアルは、複数の機械学習モデルを最高レベルの GPU パフォーマンスを順番に実行する方法を示しています。
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 4fd0c47a04b96922bf9ea6f498d54d827c5f257d
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180834"
---
# <a name="executing-multiple-ml-models-in-a-chain"></a>チェーンの複数の ML モデルを実行します。

Windows ML は、慎重に GPU のパスを最適化することによって、高パフォーマンスの負荷とモデルのチェーンの実行をサポートしています。 モデルのチェーンが順番に実行する 2 つまたは複数のモデルで定義されている、下向き、チェーンの 1 つのモデルの出力が次のモデルへの入力になります。 

Windows の ML を使用したモデルを効率的にチェーンする方法を説明するために単純な例として FNS キャンディ スタイル転送 ONNX モデルを使用してしましょう。 FNS キャンディ スタイル転送サンプル フォルダーにこの種類のモデルを見つけることができます、 [GitHub](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer)します。

ここでのという同じ FNS キャンディ モデルの 2 つのインスタンスで構成されるチェーンを実行すると**mosaic.onnx**します。 アプリケーション コードは、チェーンの最初のモデルにイメージを渡す、出力を計算し、その変換後のイメージを FNS キャンディ、最終的なイメージの生成の別のインスタンスに渡します。  

次の手順は、これを実現する方法を示しています。 Windows ML を使用します。

>[!Note]
>実際の単語のシナリオでは、2 つの異なるモデルを使用する可能性が最も高いが、これは、概念を説明するために十分なはずです。

1. 最初に、読み込む、 **mosaic.onnx**モデルを使用できます。
  ```cpp
  std::wstring filePath = L"path\\to\\mosaic.onnx"; 
  LearningModel model = LearningModel::LoadFromFilePath(filePath);
  ```

  ```cs
  string filePath = "path\\to\\mosaic.onnx";
  LearningModel model = LearningModel.LoadFromFilePath(filePath);
  ```

2. 次に、デバイスの既定の入力パラメーターとして、同じモデルを使用して GPU で 2 つの同じセッションを作成しましょう。 
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
>チェーンのパフォーマンスの利点を享受するためには、モデルのすべての同一 GPU セッションを作成する必要があります。 そうしないと、GPU からと、CPU では、パフォーマンスが低下するように、追加のデータ移動が発生します。

3. 次のコード行は各セッションのバインドを作成します。
  ```cpp
  LearningModelBinding binding1(session1);
  LearningModelBinding binding2(session2);
  ```

  ```cs
  LearningModelBinding binding1 = new LearningModelBinding(session1);
  LearningModelBinding binding2 = new LearningModelBinding(session2);
  ```

4. 次に、最初、モデルの入力をバインドします。 モデルと同じパスにあるイメージを渡します。 この例では、イメージを"fish_720.png"と呼びます。
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

5. チェーン内の次のモデルで最初のモデルの評価の出力を使用するには、空の出力を利用したテンソルの作成を使ったチェーンのマーカーがあるために、出力をバインドする必要があります。
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
>使用する必要があります、 **TensorFloat**データ型の出力をバインドするときにします。 これにより、最初のモデルの評価が完了すると発生しているから除外 tensorization も追加の GPU の回避などのキューに登録を読み込むし、2 つ目のモデルの操作をバインドします。

6. ここで、最初のモデルの評価を実行し、次のモデルの入力をその出力をバインドします。
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

7. 最後に、次のコード行を使用して両方のモデルを実行した後に生成される最終的な出力を取得してみましょう。
  ```cpp
  auto finalOutput = session2AsyncOp.get().Outputs().First().Current().Value();
  ```

  ```cs
  var finalOutput = results.Outputs.First().Value;
  ```

以上で作業は終了です。 これで、両方のモデルは、最大限に利用可能な GPU リソースの順番に実行できます。 

[!INCLUDE [help](../includes/get-help.md)]
