---
author: rosanevallim
title: Windows の ML の ONNX モデルを取得します。
description: Windows の ML は、さまざまな ML フレームワークとツールの間でのモデルを交換することができます、ONNX 形式でモデルを評価します。
ms.author: rovalli
ms.date: 2/20/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: adc7bd875a40ebd44043799ab6e52fe7252e3f15
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474099"
---
# <a name="get-onnx-models-for-windows-ml"></a>Windows の ML の ONNX モデルを取得します。

Windows の ML でのモデルの評価、[オープン ニューラル ネットワーク Exchange (ONNX)](https://onnx.ai)形式。 ONNX は ML モデルをオープン フォーマット間さまざまなモデルを交換することができます[ML フレームワークとツール](http://onnx.ai/supported-tools)します。

> [!IMPORTANT]
> Windows の ML ONNX モデルを必要と[バージョン 1.2](https://github.com/onnx/onnx/tree/rel-1.2.2)またはそれ以降。

Windows の ML で使用するには ONNX モデルを取得するには、次のことができます。

- 事前トレーニング済みから ONNX モデルをダウンロード、 [ONNX モデル Zoo](https://github.com/onnx/models)します。
- などのサービスを使用したモデルをトレーニング[Azure Custom Vision Service](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier)、 [Azure Machine Learning](https://azure.microsoft.com/overview/machine-learning/)、または[VS Tools for AI](https://visualstudio.microsoft.com/downloads/ai-tools-vs/)、および ONNX 形式にエクスポートします。
    - Custom Vision を使用してクラウドでのモデルをトレーニングする方法については、チェック アウト[チュートリアル。Custom Vision から ONNX モデルを使用して Windows ML (プレビュー) を使用した](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml)します。
- その他の ML フレームワークに ONNX 形式にトレーニングされたモデルを変換[WinMLTools](convert-model-winmltools.md)コンバーターまたは[ONNX チュートリアル](https://github.com/onnx/tutorials)します。

ONNX モデルを作成したらが[モデルを統合](integrate-model.md)にアプリのコードで、次に、使用できるようマシン学習、Windows アプリとデバイス。

[!INCLUDE [help](includes/get-help.md)]
