---
author: eliotcowley
title: PyTorch を持つモデルをトレーニングします。
description: PyTorch を ONNX モデルをトレーニングする方法について説明します。
ms.author: elcowle
ms.date: 11/5/2018
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows machine learning、pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 3077447e06e3898328a1f5f8939efec4288aefe4
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474309"
---
# <a name="train-a-model-with-pytorch"></a>PyTorch を持つモデルをトレーニングします。

[PyTorch](https://pytorch.org/)フレームワークでは、ローカルまたはクラウドで、モデルのトレーニングし、Windows Machine Learning でローカルで実行する ONNX ファイルとして、モデルをダウンロードすることができます。

## <a name="train-locally"></a>ローカルでトレーニングします。

参照してください[mnist.py](https://github.com/Azure/MachineLearningNotebooks/blob/master/onnx/mnist.py) MNIST トレーニングする方法の例については、Azure/MachineLearningNotebooks リポジトリでモデルを使用してローカル PyTorch します。

詳細については、PyTorch、PyTorch を参照してください。[チュートリアル](https://pytorch.org/tutorials/)と[ドキュメント](https://pytorch.org/docs/stable/index.html)します。

## <a name="train-in-the-cloud"></a>クラウドでのトレーニングします。

Azure Machine Learning と PyTorch、クラウドでモデルをトレーニングし、Windows Machine Learning でローカルで実行することをダウンロードできます。 [Azure/MachineLearningNotebooks GitHub リポジトリ](https://github.com/Azure/MachineLearningNotebooks)Azure ML でのいくつかのサンプルとチュートリアルを持つはほとんど[Jupyter notebook](https://jupyter.org/)します。 参照してください、 [README](https://github.com/Azure/MachineLearningNotebooks/blob/master/README.md) Azure Notebook または独自の Jupyter Notebook サーバーを Azure ML のこれらのチュートリアルを実行する方法についてはします。

開くことができますな設定がすべてを取得した後、 [MNIST 手書き数字を使用した分類 ONNX と Azure ML](https://github.com/Azure/MachineLearningNotebooks/blob/master/onnx/onnx-train-pytorch-aml-deploy-mnist.ipynb)ノートブックおよび PyTorch と Azure ML を使用してモデル化、MNIST トレーニングする方法についてのチュートリアルに従ってください。 (省略できます、 **web サービスとしてデプロイ**セクション実行モデルを WinML を使用している場合)。

[!INCLUDE [help](includes/get-help.md)]
