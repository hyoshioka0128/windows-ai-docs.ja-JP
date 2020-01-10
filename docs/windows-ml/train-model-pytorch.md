---
title: PyTorch を使用してモデルをトレーニングし、ONNX にエクスポートする
description: PyTorch で ONNX モデルをトレーニングする方法について説明します。
ms.date: 7/10/2019
ms.topic: article
keywords: windows 10、windows ai、windows ml、winml、windows machine learning、pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 7aa1091cf3622f532c6601a040fad5c80746d6b3
ms.sourcegitcommit: ecd33843dd548e443a1292d6a22e1a4029298944
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737405"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>PyTorch を使用してモデルをトレーニングし、ONNX にエクスポートする

[PyTorch](https://pytorch.org/) framework と[Azure Machine Learning](https://azure.microsoft.com/services/machine-learning-service/)では、クラウドでモデルをトレーニングし、ONNX ファイルとしてダウンロードして、Windows Machine Learning でローカルに実行することができます。

## <a name="train-the-model"></a>モデルのトレーニング

Azure ML を使用すると、クラウドで PyTorch モデルをトレーニングし、迅速なスケールアウトやデプロイなどのメリットを得ることができます。 詳細については[、「Azure Machine Learning による大規模な PyTorch モデルのトレーニングと登録](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch)」を参照してください。

## <a name="export-to-onnx"></a>ONNX にエクスポートする

モデルのトレーニングが完了したら、ONNX ファイルとしてエクスポートできます。これにより、Windows ML でローカルに実行できるようになります。 PyTorch からネイティブでエクスポートする方法については、「 [Export PyTorch model For WINDOWS ML](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchForWinML.md) 」を参照してください。


## <a name="integrate-with-windows-ml"></a>Windows ML との統合

モデルを ONNX にエクスポートしたら、それを Windows ML アプリケーションに統合する準備ができています。 Windows ML はいくつかの異なるプログラミング言語で使用できるため、使い慣れた言語のチュートリアルをご確認ください。

* : [Windows Machine Learning UWP アプリケーションを作成しC#ます ()](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)  **C#**

* **Python:** [python を使用して Windows Machine Learning アプリケーションを作成する](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* : [Windows Machine Learning デスクトップアプリケーション (C++) を作成し](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)**ます。 C++**

[!INCLUDE [help](../includes/get-help.md)]
