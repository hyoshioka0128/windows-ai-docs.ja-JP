---
author: eliotcowley
title: モデルを読み込む
description: 使用する Windows Machine Learning のアプリケーションに、ONNX モデルを読み込む方法について説明します。
ms.author: elcowle
ms.date: 2/14/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: eb0df76a0a925b38d8b7fbb6da3fcddcfaa08648
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473859"
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
> モデルの読み込み時間がかかる、いないを呼び出すためご注意くださいことができます、**ロード***、UI スレッドからメソッド。

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

[!INCLUDE [help](includes/get-help.md)]
