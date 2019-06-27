---
author: rosanevallim
title: ONNX モデル
description: Windows の ML は、さまざまな ML フレームワークとツールの間でのモデルを交換することができます、ONNX 形式でモデルを評価します。
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows machine learning、onnx
ms.localizationpriority: medium
ms.openlocfilehash: 35baba048337402f3ed8ceafe79115423962bcba
ms.sourcegitcommit: 12993277cf7f97c9c6a02908e4a4f1f91b689edb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66740495"
---
# <a name="onnx-models"></a>ONNX モデル

Windows Machine Learning でモデルをサポートする、[オープン ニューラル ネットワーク Exchange (ONNX)](https://onnx.ai/)形式。 ONNX は ML モデルをオープン フォーマット間さまざまなモデルを交換することができます[ML フレームワークとツール](https://onnx.ai/supported-tools)します。

ONNX 形式でモデルを取得できるいくつかの方法を含みます。

- [ONNX モデル Zoo](https://github.com/onnx/models):さまざまな種類のタスクのいくつかの事前トレーニング済み ONNX モデルが含まれています。 Windows ML でサポートされているバージョンをダウンロードして、すぐに参照してください!

- [ML トレーニング フレームワークからのネイティブのエクスポート](https://onnx.ai/supported-tools):いくつかのトレーニング フレームワークでは、ONNX、Chainer、Caffee2、ONNX 形式の特定のバージョンに、トレーニングされたモデルを保存することができます、PyTorch などにネイティブのエクスポート機能をサポートします。 さらなどのサービス[Azure Machine Learning サービス](https://azure.microsoft.com/services/machine-learning-service/)と[Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier)もネイティブ ONNX エクスポートを提供します。
    - トレーニングし、カスタムのビジョンを使用して、クラウドに ONNX モデルをエクスポートする方法については、チェック アウト[チュートリアル。Custom Vision から ONNX モデルを使用して Windows ML (プレビュー) を使用した](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml)します。

- [WinMLTools を使用して既存のモデルを変換](https://docs.microsoft.com/windows/ai/windows-ml/convert-model-winmltools):この Python パッケージには、トレーニング フレームワークのいくつかの形式から ONNX に変換するモデルができます。 開発者は、Windows アプリケーションの対象のビルドによって、モデルに変換したい ONNX のバージョンを指定できます。 Python に慣れていない場合は使用できます[Windows ML の UI ベースのダッシュ ボード](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard)ほんの数回のクリックで、モデルを簡単に変換します。

> [!IMPORTANT]
> すべての ONNX バージョンは、Windows の ML でサポートされます。 アプリケーションの対象となる Windows のバージョンで正式にサポートされる ONNX バージョンを知るために確認してください[ONNX バージョンと Windows ビルド](onnx-versions.md)します。

ONNX モデルを作成したらが[モデルを統合](https://docs.microsoft.com/windows/ai/windows-ml/integrate-model)アプリのコードに使用できるようマシン学習、Windows アプリとデバイス。

[!INCLUDE [help](../includes/get-help.md)]
