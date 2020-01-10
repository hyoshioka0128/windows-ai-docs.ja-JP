---
author: rosanevallim
title: ONNX モデル
description: Windows ML は、モデルを ONNX 形式で評価し、さまざまな ML フレームワークとツール間でモデルを交換できるようにします。
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: windows 10、windows ai、windows ml、winml、windows machine learning、onnx
ms.localizationpriority: medium
ms.openlocfilehash: d1b43ca0f0ea47b81ff29e3e196fc77c5319c647
ms.sourcegitcommit: ecd33843dd548e443a1292d6a22e1a4029298944
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737415"
---
# <a name="onnx-models"></a>ONNX モデル

Windows Machine Learning では、 [Open ニューラル Network Exchange (ONNX)](https://onnx.ai/)形式のモデルがサポートされています。 ONNX は ML モデルのオープン形式であり、さまざまな[ml フレームワークとツール](https://onnx.ai/supported-tools)間でモデルを交換できます。

ONNX 形式でモデルを取得するには、次のようないくつかの方法があります。

- [ONNX Model Zoo](https://github.com/onnx/models): さまざまな種類のタスクに対して事前トレーニング済みの ONNX モデルがいくつか含まれています。 Windows ML でサポートされているバージョンをダウンロードしてください。

- [ML トレーニングフレームワークからのネイティブエクスポート](https://onnx.ai/supported-tools): いくつかのトレーニングフレームワークでは、Chainer、Caffee2、PyTorch などの ONNX にネイティブエクスポート機能がサポートされており、トレーニング済みのモデルを ONNX 形式の特定のバージョンに保存することができます。 さらに、 [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning-service/)や[Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier)などのサービスは、ネイティブ ONNX のエクスポートも提供します。
    - Custom Vision を使用してクラウドでの ONNX モデルのトレーニングとエクスポートを行う方法については、「[チュートリアル: WINDOWS ML での ONNX Custom Vision モデルの使用 (プレビュー)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml)」を参照してください。

- [WinMLTools を使用した既存のモデルの変換](https://docs.microsoft.com/windows/ai/windows-ml/convert-model-winmltools): この Python パッケージでは、モデルを複数のトレーニングフレームワーク形式から ONNX に変換できます。 開発者は、アプリケーションの対象となる Windows のビルドに応じて、モデルを変換する ONNX のバージョンを指定できます。 Python に慣れていない場合は、 [WINDOWS ML の UI ベースのダッシュボード](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard)を使用して、わずか数回のクリックで簡単にモデルを変換できます。

> [!IMPORTANT]
> すべての ONNX バージョンが Windows ML でサポートされているわけではありません。 アプリケーションの対象となる Windows バージョンで正式にサポートされている ONNX のバージョンを確認するには、 [ONNX のバージョンと windows ビルド](onnx-versions.md)を確認してください。

ONNX モデルを作成したら、モデルをアプリのコードに[統合](https://docs.microsoft.com/windows/ai/windows-ml/integrate-model)します。これにより、Windows アプリとデバイスで machine learning を使用できるようになります。

[!INCLUDE [help](../includes/get-help.md)]
