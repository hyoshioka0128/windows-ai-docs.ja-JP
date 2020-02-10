---
title: PyTorch を使用してモデルをトレーニングし、ONNX にエクスポートする
description: PyTorch を使用して ONNX モデルをトレーニングする方法について説明します。
ms.date: 7/10/2019
ms.topic: article
keywords: Windows 10、Windows AI、Windows ML、WinML、Windows Machine Learning、PyTorch
ms.localizationpriority: medium
ms.openlocfilehash: 7aa1091cf3622f532c6601a040fad5c80746d6b3
ms.sourcegitcommit: ecd33843dd548e443a1292d6a22e1a4029298944
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737405"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>PyTorch を使用してモデルをトレーニングし、ONNX にエクスポートする

[PyTorch](https://pytorch.org/) フレームワークと [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning-service/) を使用すると、クラウド内のモデルをトレーニングし、それを ONNX ファイルとしてダウンロードして Windows Machine Learning でローカルに実行できます。

## <a name="train-the-model"></a>モデルをトレーニングする

Azure ML を使用すると、クラウド内の PyTorch モデルをトレーニングすることにより、迅速なスケールアウトやデプロイなどの多くの利点を得ることができます。 詳細については、[Azure Machine Learning を使用した PyTorch モデルの大規模なトレーニングと登録](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch)に関するページを参照してください。

## <a name="export-to-onnx"></a>ONNX にエクスポートする

モデルをトレーニングしたら、それを ONNX ファイルとしてエクスポートして Windows ML でローカルに実行できます。 PyTorch からネイティブにエクスポートする方法については、[Windows ML での PyTorch モデルのエクスポート](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchForWinML.md)に関するページを参照してください。


## <a name="integrate-with-windows-ml"></a>Windows ML と統合する

モデルを ONNX にエクスポートすると、それを Windows ML アプリケーションに統合する準備が整います。 Windows ML はいくつかの異なるプログラミング言語で使用できるため、最も使い慣れている言語のチュートリアルを確認してください。

* **C#:** [Windows Machine Learning の UWP アプリケーションの作成 (C#)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)

* **Python:** [Python での Windows Machine Learning アプリケーションの作成](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* **C++:** [Windows Machine Learning のデスクトップ アプリケーションの作成 (C++)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)

[!INCLUDE [help](../includes/get-help.md)]
