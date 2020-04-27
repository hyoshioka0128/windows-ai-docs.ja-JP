---
author: rosanevallim
title: ONNX モデル
description: Windows ML は ONNX 形式のモデルを評価するため、さまざまな ML フレームワークおよびツールの間でモデルを交換できます。
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: Windows 10、Windows AI、Windows ML、WinML、Windows Machine Learning、ONNX
ms.localizationpriority: medium
ms.openlocfilehash: d1b43ca0f0ea47b81ff29e3e196fc77c5319c647
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "75737415"
---
# <a name="onnx-models"></a>ONNX モデル

Windows Machine Learning は、[Open Neural Network Exchange (ONNX)](https://onnx.ai/) 形式のモデルをサポートしています。 ONNX は ML モデルのオープンな形式であるため、さまざまな [ML フレームワークおよびツール](https://onnx.ai/supported-tools)の間でモデルを交換できます。

ONNX 形式のモデルは、次に示すようないくつかの方法で取得できます。

- [ONNX Model Zoo](https://github.com/onnx/models): さまざまな種類のタスクのためのいくつかの事前トレーニング済みの ONNX モデルが含まれています。 Windows ML でサポートされているバージョンをダウンロードすれば、すぐに使用できます。

- [ML トレーニング フレームワークからのネイティブ エクスポート](https://onnx.ai/supported-tools): Chainer、Caffee2、PyTorch などのいくつかのトレーニング フレームワークでは ONNX へのネイティブ エクスポート機能をサポートしているため、トレーニング済みのモデルを ONNX 形式の特定のバージョンに保存できます。 さらに、[Azure Machine Learning](https://azure.microsoft.com/services/machine-learning-service/) や [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier) などのサービスでもネイティブな ONNX エクスポートが提供されます。
    - Custom Vision を使用してクラウド内の ONNX モデルをトレーニングおよびエクスポートする方法については、「[チュートリアル: Custom Vision からエクスポートされた ONNX モデルを Windows ML (プレビュー) で使用する](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml)」を確認してください。

- [WinMLTools を使用して既存のモデルを変換する](https://docs.microsoft.com/windows/ai/windows-ml/convert-model-winmltools): この Python パッケージを使用すると、モデルをいくつかのトレーニング フレームワーク形式から ONNX に変換できます。 開発者は、アプリケーションが対象としている Windows のビルドに応じて、モデルをどのバージョンの ONNX に変換するかを指定できます。 Python に詳しくない場合は、[Windows ML の UI ベースのダッシュボード](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard)を使用して、数回クリックするだけでモデルを簡単に変換できます。

> [!IMPORTANT]
> すべての ONNX バージョンが Windows ML でサポートされているわけではありません。 アプリケーションが対象としている Windows バージョンでどの ONNX バージョンが正式にサポートされているかを調べるには、「[ONNX バージョンと Windows ビルド](onnx-versions.md)」を確認してください。

ONNX モデルを作成したら、アプリのコードに[そのモデルを統合](https://docs.microsoft.com/windows/ai/windows-ml/integrate-model)すると、Windows アプリおよびデバイスで機械学習を使用できるようになります。

[!INCLUDE [help](../includes/get-help.md)]
