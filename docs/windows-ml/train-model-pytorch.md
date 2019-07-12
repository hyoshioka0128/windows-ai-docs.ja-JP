---
author: eliotcowley
title: PyTorch ONNX へのエクスポートとモデルをトレーニングします。
description: PyTorch を ONNX モデルをトレーニングする方法について説明します。
ms.author: elcowle
ms.date: 7/10/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows machine learning、pytorch
ms.localizationpriority: medium
ms.openlocfilehash: 6c1f9ac16bfa2359b01b26ecd297b9087caa8c14
ms.sourcegitcommit: 785057dc180cb252ce63460efaaff321e046a0dd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804780"
---
# <a name="train-a-model-with-pytorch-and-export-to-onnx"></a>PyTorch ONNX へのエクスポートとモデルをトレーニングします。

[PyTorch](https://pytorch.org/)フレームワークと[Azure Machine Learning サービス](https://azure.microsoft.com/services/machine-learning-service/)クラウドでのモデルのトレーニングし、Windows Machine Learning でローカルで実行するための ONNX ファイルとしてダウンロードできます。

## <a name="train-the-model"></a>モデルをトレーニングします。

Azure ML には迅速なスケール アウト、展開、およびその他のメリットを得る、クラウドで PyTorch モデルをトレーニングできます。 参照してください[PyTorch がある Azure Machine Learning サービスで、大規模モデル トレーニングと登録](https://docs.microsoft.com/azure/machine-learning/service/how-to-train-pytorch)詳細についてはします。

## <a name="export-to-onnx"></a>ONNX へのエクスポートします。

モデルをトレーニングすると、エクスポートできます ONNX ファイルとして Windows ML を使用したローカルで実行できるようにします。 エクスポート前に、ただし、チェック[ビルド ONNX バージョンと Windows](https://docs.microsoft.com/windows/ai/windows-ml/onnx-versions)サポートされている ONNX バージョンを確認する対象にしている Windows のビルド時にします。

エクスポートする準備ができたらを参照してください。 [ONNX PyTorch からのエクスポート モデル](https://github.com/onnx/tutorials/blob/master/tutorials/PytorchOnnxExport.ipynb)します。

## <a name="integrate-with-windows-ml"></a>Windows の ML との統合します。

ONNX モデルをエクスポートしたら後、は、Windows の ML アプリケーションに統合する準備ができました。 Windows の ML がいくつかの異なるプログラミング言語で利用可能なのでに最も慣れている言語のチュートリアル。

* **C# の場合:** [Windows Machine Learning の UWP アプリケーションの作成 (C#)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-uwp)

* **Python:** [Python を使用した Windows Machine Learning アプリケーションを作成します。](https://github.com/Microsoft/xlang/tree/master/samples/python/winml_tutorial)

* **C++:** [Windows Machine Learning のデスクトップ アプリケーションの作成 (C++)](https://docs.microsoft.com/windows/ai/windows-ml/get-started-desktop)

[!INCLUDE [help](../includes/get-help.md)]
