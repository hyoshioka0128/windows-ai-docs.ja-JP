---
author: eliotcowley
title: モデルを読み込む
description: 使用する Windows Machine Learning のアプリケーションに、ONNX モデルを読み込む方法について説明します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: a65eb38f666b2e2c2d72290804cb25430ac7ca8a
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181914"
---
# <a name="load-a-model"></a>モデルを読み込む

> [!IMPORTANT]
> Windows Machine Learning では、ONNX モデル、バージョン 1.2 以降が必要です。

したら[ONNX モデルをトレーニングの取得](get-onnx-model.md)、.onnx モデル ファイルは、アプリケーションで配布されます。 APPX パッケージに .onnx ファイルを含めることも、デスクトップ アプリは、可能性があるアプリがハード ドライブにアクセスできる任意の場所。

いくつかの方法で静的メソッドを使用してモデルを読み込む、 [LearningModel](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel)クラス。

* [LearningModel.LoadFromStreamAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstreamasync)
* [LearningModel.LoadFromStream](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstream)
* [LearningModel.LoadFromStorageFileAsync](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromstoragefileasync)
* [LearningModel.LoadFromFilePath](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodel.loadfromfilepath)

**LoadFromStream*** メソッドは、モデル、送信元の場所をより細かく制御するアプリケーションを使用します。 たとえば、アプリがディスク上で暗号化モデルがありのいずれかを呼び出す前にメモリ内にのみ暗号化を解除する選択でした、 **LoadFromStream*** メソッド。 その他のオプションには、ネットワーク共有またはその他のメディアからのモデルのストリームの読み込みが含まれます。

> [!TIP]
> モデルの読み込み時間がかかる、いないを呼び出すためご注意くださいことができます、**ロード**\*、UI スレッドからメソッド。

次の例では、アプリケーションに、モデルを読み込む方法を示しています。

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

* 次に：[セッションを作成します。](create-a-session.md)

[!INCLUDE [help](../includes/get-help.md)]
