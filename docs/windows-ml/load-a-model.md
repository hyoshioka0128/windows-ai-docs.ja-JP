---
title: モデルを読み込む
description: 使用する Windows Machine Learning 用のアプリケーションに ONNX モデルを読み込む方法について説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: c0fd10c4f970659d4560fbb4b4d259c6d30b11c4
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156601"
---
# <a name="load-a-model"></a>モデルを読み込む

> [!IMPORTANT]
> Windows Machine Learning には、バージョン 1.2 以降の ONNX モデルが必要です。

トレーニング済みの [ONNX モデルを入手](get-onnx-model.md)したら、アプリと一緒に ONNX モデル ファイルを配布します。 .onnx ファイルは appx パッケージに含めることができます。また、デスクトップ アプリの場合は、ハード ドライブ上のアプリがアクセスできる任意の場所に置くことができます。

モデルを読み込む方法は複数あり、[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel) クラスの以下の静的メソッドを使用します。

* [LearningModel.LoadFromStreamAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstreamasync)
* [LearningModel.LoadFromStream](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstream)
* [LearningModel.LoadFromStorageFileAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstoragefileasync)
* [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath)

**LoadFromStream*** メソッドを使用すると、アプリケーションでモデルの取得元をより細かく制御できます。 たとえば、モデルをディスク上で暗号化し、メモリ内でのみ暗号化を解除してから、**LoadFromStream*** メソッドのいずれかを呼び出すことを選択できます。 その他のオプションとしては、ネットワーク共有や他のメディアからのモデル ストリームの読み込みがあります。

> [!TIP]
> モデルの読み込みには時間がかかる場合があるため、UI スレッドから **Load*** メソッドを呼び出さないように注意してください。

次の例は、アプリケーションにモデルを読み込む方法を示しています。

```cs
private async LearningModel LoadModelAsync(string modelPath)
{
    // Load and create the model
    var modelFile = await StorageFile.GetFileFromApplicationUriAsync(
        new Uri(modelPath));

    LearningModel model =
        await LearningModel.LoadFromStorageFileAsync(modelFile);

    return model;
}
```

## <a name="see-also"></a>関連項目

* 次の手順:[セッションを作成する](create-a-session.md)

[!INCLUDE [help](../includes/get-help.md)]
