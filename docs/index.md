---
author: rosanevallim
title: Windows Machine Learning
description: Windows ML を使うと、Windows アプリケーション内でトレーニング済みの機械学習モデルを利用できます。
ms.author: rovalli
ms.date: 12/12/2018
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 011cf35c131b5f33891bb51722cb5f544d3e5193
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59473729"
---
# <a name="windows-machine-learning"></a>Windows Machine Learning

Windows ML を使うと、Windows アプリにトレーニング済みの機械学習モデルを統合できます。

![Windows ML のグラフィックス](images/winml-graphic.png)

## <a name="overview"></a>概要

:::row:::
    :::column:::
    Windows ML を使うと、Windows アプリ (C#、C++、JavaScript) 内でトレーニング済みの機械学習モデルを利用できます。 Windows ML の推論エンジンでは、トレーニング済みのモデルの評価がローカルの Windows デバイス上で行われるので、接続、帯域幅、データのプライバシーを心配する必要がありません。 また、CPU と GPU のためのハードウェア最適化により高パフォーマンスが実現しており、短時間で評価結果が得られます。

    Windows ML の最新の機能と修正プログラムについては、「[リリース ノート](release-notes.md)」を参照してください。
    :::column-end:::
    :::column:::
        ![windows ml layers](images/overview-diagram.png)
    :::column-end:::
:::row-end:::

次のビデオは、Windows Machine Learning の概要を簡単に紹介したものです。

<br/>

> [!VIDEO https://www.youtube.com/embed/riGxT0Pd6IA]

## <a name="develop"></a>開発

![Windows ML の開発者向けフロー](images/winml-flow.png)

Windows ML を使ったアプリを作成する方法は次のとおりです。

1. [トレーニング済みの ONNX モデルを入手する](get-onnx-model.md)か、他の ML フレームワークによるトレーニングを経たモデルを [WinMLTools](convert-model-winmltools.md) を使って変換します。
1. アプリに ONNX モデル ファイルを追加します。
1. アプリのコードに[モデルを統合](integrate-model.md)します。
1. Windows デバイス上で実行します。

Windows ML が実際に動作しているところを確認する場合には、GitHub の [Windows-Machine-Learning](https://github.com/Microsoft/Windows-Machine-Learning/tree/master) リポジトリにあるサンプル アプリをお試しください。 Windows ML の使い方の詳細については、Microsoft が提供しているドキュメントを参照してください。

## <a name="other-machine-learning-solutions-from-microsoft"></a>Microsoft の他の機械学習ソリューション

Microsoft では、お客様のニーズに応じてさまざまな機械学習ソリューションを提供しています。 ソリューションはクラウド内で運用するものもあれば、オンプレミスやローカル デバイスで運用するものもあります。 詳細については、「[Microsoft の機械学習製品とは](https://docs.microsoft.com/azure/machine-learning/service/overview-more-machine-learning)」を参照してください。

[!INCLUDE [help](includes/get-help.md)]
