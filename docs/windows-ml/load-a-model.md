---
title: モデルを読み込む
description: Windows Machine Learning で使用するために、アプリケーションに ONNX モデルを読み込む方法について説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: c0fd10c4f970659d4560fbb4b4d259c6d30b11c4
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156601"
---
# <a name="load-a-model"></a>モデルを読み込む

> [!IMPORTANT]
> Windows Machine Learning には、バージョン1.2 以降の ONNX モデルが必要です。

トレーニング済みの[ONNX モデルを入手](get-onnx-model.md)したら、ONNX モデルファイルをアプリと共に配布します。 Onnx ファイルは APPX パッケージに含めることができます。また、デスクトップアプリの場合は、アプリがハードドライブにアクセスできる任意の場所に置くことができます。

[LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)クラスの静的メソッドを使用してモデルを読み込むには、いくつかの方法があります。

* [LearningModel.LoadFromStreamAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstreamasync)
* [LearningModel.LoadFromStream](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstream)
* [LearningModel.LoadFromStorageFileAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstoragefileasync)
* [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath)

**LoadFromStream*** メソッドを使用すると、アプリケーションはモデルの取得元をより細かく制御できます。 たとえば、アプリでは、モデルをディスク上で暗号化し、 **LoadFromStream*** メソッドの1つを呼び出す前にメモリ内でのみ暗号化を解除することを選択できます。 その他のオプションとしては、ネットワーク共有や他のメディアからのモデルストリームの読み込みがあります。

> [!TIP]
> モデルの読み込み時間がかかる、いないを呼び出すためご注意くださいことができます、**ロード**\*、UI スレッドからメソッド。

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
