---
title: PyTorch を使用してモデルをトレーニングし、ONNX にエクスポートする
description: PyTorch で ONNX モデルをトレーニングする方法について説明します。
ms.date: 7/10/2019
ms.topic: article
keywords: windows 10、windows ai、windows ml、winml、windows machine learning、pytorch
ms.localizationpriority: medium
ms.openlocfilehash: d2d20b20ab790247ad7746d0cf8f221f9276e823
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156325"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>PyTorch を使用してモデルをトレーニングし、ONNX にエクスポートする

[PyTorch](https://pytorch.org/) framework と[Azure Machine Learning サービス](https://azure.microsoft.com/services/machine-learning-service/)を使用すると、クラウドでモデルをトレーニングし、ONNX ファイルとしてダウンロードして、Windows Machine Learning でローカルに実行することができます。

## <a name="train-the-model"></a>モデルのトレーニング

Azure ML を使用すると、クラウドで PyTorch モデルをトレーニングし、迅速なスケールアウトやデプロイなどのメリットを得ることができます。 詳細については[、「Azure Machine Learning サービスを使用した大規模な PyTorch モデルのトレーニングと登録](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch)」を参照してください。

## <a name="export-to-onnx"></a>ONNX へのエクスポート

モデルのトレーニングが完了したら、ONNX ファイルとしてエクスポートできます。これにより、Windows ML でローカルに実行できるようになります。 PyTorch からネイティブでエクスポートする方法については、「 [Export PyTorch model For WINDOWS ML](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchForWinML.md) 」を参照してください。


## <a name="integrate-with-windows-ml"></a>Windows ML との統合

モデルを ONNX にエクスポートしたら、それを Windows ML アプリケーションに統合する準備ができています。 Windows ML はいくつかの異なるプログラミング言語で使用できるため、使い慣れた言語のチュートリアルをご確認ください。

* **C#:** [Windows Machine Learning UWP アプリケーションを作成するC#()](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)

* **Python**[Python を使用して Windows Machine Learning アプリケーションを作成する](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* **C++:** [Windows Machine Learning デスクトップアプリケーションを作成するC++()](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)

[!INCLUDE [help](../includes/get-help.md)]
