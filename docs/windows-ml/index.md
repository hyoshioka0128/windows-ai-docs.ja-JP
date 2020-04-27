---
author: rosanevallim
title: Windows Machine Learning の概要
description: Windows ML を使うと、Windows アプリケーション内でトレーニング済みの機械学習モデルを利用できます。
ms.author: rovalli
ms.date: 6/5/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4837648d23a21ea15ea27493ccba5307f81af0a0
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "74782634"
---
# <a name="windows-machine-learning"></a>Windows Machine Learning

Windows ML を使用して Windows アプリに AI を実装します。Windows ML は、Windows デバイス上で ML 推論を実行するための信頼性の高い高パフォーマンス API です。

![Windows ML のグラフィックス](../images/winml-graphic.png)

## <a name="overview"></a>概要

Windows ML を使用すると、開発者は Windows 10 のローカル デバイスまたは Windows Server 2019 マシン上のいずれかで、C#、C++、JavaScript、または Python で記述された Windows アプリ内のトレーニング済みの ML モデルを使用することができます。 トレーニング済みの ML モデルをアプリケーション コードに組み込むプロセスはシンプルで、次に示すいくつかの単純な手順のみが必要です。

![トレーニング環境, モデル参照の追加, アプリケーション, Windows ML](../images/winml-flow.png)

1. トレーニング済みの Open Neural Network Exchange (ONNX) モデルを取得するか、別の ML フレームワークでトレーニングされたモデルを [WinMLTools](convert-model-winmltools.md) で ONNX に変換します。

2. ONNX モデル ファイルをアプリケーションに追加します。または他の何らかの方法でターゲット デバイス上で使用できるようにします。

3. モデルをアプリケーション コードに統合し、アプリケーションをビルドして展開します。

:::row:::
    :::column:::
    アプリケーションを実行すると、Windows ML ランタイム (ONNX モデル推論エンジンを含む) は Windows 10 デバイス (またはサーバー展開を対象とする場合は Windows Server 2019) 上のトレーニング済みモデルを評価します。 Windows ML がハードウェア アブストラクションを処理するため、開発者は CPU や GPU、さらに将来は AI アクセラレータなどを含む広い範囲のシリコンを対象にすることができます。 Windows ML ハードウェア アクセラレータは [DirectML](https://docs.microsoft.com/windows/desktop/direct3d12/dml) 上に構築されます。これは ML 推論を実行するための高パフォーマンスで低レベルの API で、DirectX ファミリの一部です。
    :::column-end:::
    :::column:::
        ![Windows ML のレイヤー](../images/overview-diagram.svg)
    :::column-end:::
:::row-end:::

Windows ML は、開発者に次の利点をもたらします。

- **開発の容易さ**: Windows ML を最新バージョンの Windows 10 および Windows Server 2019 に組み込んだら、あと必要なのは Visual Studio とトレーニング済みの ONNX モデルだけで、これらは Windows アプリケーションと一緒に配布できます。

- **幅広いハードウェア サポート**: Windows ML を使用することによって、ML ワークロードを 1 回記述すれば、さまざまなハードウェア ベンダーやシリコンの種類 (CPU、GPU、AI アクセラレータなど) にわたって高度に最適化されたパフォーマンスを自動的に得ることができます。 さらに、Windows ML では、サポートされているすべてのハードウェアで一貫した動作が保証されます。

- **待ち時間が短く結果をリアルタイムで利用可能**: Windows デバイスの処理機能を使用して ML モデルを評価でき、画像やビデオなどの大きなデータ ボリュームをローカルでリアルタイムに分析できます。 分析結果は、ゲーム エンジンなどのパフォーマンスが集中するワークロードや、検索のインデックス作成などのバックグラウンド タスクですぐに効率的に使用できます。

- **柔軟性の向上**: Windows デバイス上で ML モデルをローカルに評価するオプションを使用すると、幅広いシナリオに対処できます。 たとえば ML モデルの評価を、デバイスがオフラインになっているときや、接続が断続的になったときに実行できます。 また、プライバシーやデータの主権の問題により、すべてのデータをクラウドに送信できないシナリオに対処することもできます。

- **運用コストの削減**: ML モデルは継続的な改善が必要な場合もあるため、ML モデルをクラウドでトレーニングし、Windows デバイスでローカルに評価すれば、最小限のデータのみがクラウドに送信されるため帯域幅コストが大幅に節約できます。 さらに、サーバー内に ML モデルを展開するシナリオでは、開発者は Windows ML ハードウェア アクセラレータを利用してモデル サービスを高速化することで、ワークロードを処理するために必要なマシンの量を減らすことができます。

Windows ML が実際に動作しているところを確認する場合には、[GitHub の Windows-Machine-Learning リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)にあるサンプル アプリをお試しください。

Windows ML の最新の機能と修正プログラムについては、「[リリース ノート](release-notes.md)」を参照してください。

次のビデオは、Windows Machine Learning の概要を簡単に紹介したものです。

<br/>

> [!VIDEO https://www.youtube.com/embed/riGxT0Pd6IA]

## <a name="other-machine-learning-solutions-from-microsoft"></a>Microsoft の他の機械学習ソリューション

Microsoft では、お客様のニーズに応じてさまざまな機械学習ソリューションを提供しています。 ソリューションはクラウド内で運用するものもあれば、オンプレミスやローカル デバイスで運用するものもあります。 詳細については、「[Microsoft の機械学習製品とは](https://docs.microsoft.com/azure/machine-learning/service/overview-more-machine-learning)」を参照してください。

[!INCLUDE [help](../includes/get-help.md)]
