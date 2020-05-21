---
author: rosanevallim
title: Windows Machine Learning の概要
description: Windows ML を使うと、Windows アプリケーション内でトレーニング済みの機械学習モデルを利用できます。
ms.author: rovalli
ms.date: 5/29/2020
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: bd46d7864e64a6fcc1466836fac084e53cac18b9
ms.sourcegitcommit: f41fad7e6b6280bbbaf4157703f03fb7f23de676
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631849"
---
# <a name="windows-machine-learning"></a>Windows Machine Learning

Windows ML を使用して Windows アプリに Machine Learning を実装します。Windows ML は、Windows デバイスにハードウェア アクセラレータ対応の ML 推論をデプロイするための信頼性の高い高パフォーマンス API です。 

![Windows ML のグラフィックス](../images/winml-graphic.png)

## <a name="overview"></a>概要

Windows ML は、最新バージョンの Windows 10 および Windows Server 2019 に組み込まれており、また Windows 8.1 までのダウンレベルに対応するために [NuGet パッケージ](https://aka.ms/windowsmlredist) としても提供されています。 Windows ML は、開発者に次の利点をもたらします。

- **開発の容易さ:** Windows ML を最新バージョンの Windows 10 および Windows Server 2019 に組み込んだら、あと必要なのは Visual Studio とトレーニング済みの ONNX モデルだけで、これらは Windows アプリケーションと一緒に配布できます。 また、AI ベースの機能を以前のバージョンの Windows (8.1 まで) に配信する必要がある場合は、アプリケーションと共に配布できる NuGet パッケージとして Windows ML を使用することもできます。

- **幅広いハードウェア サポート:** Windows ML を使用することによって、ML ワークロードを 1 回記述すれば、さまざまなハードウェア ベンダーやシリコンの種類 (CPU、GPU、AI アクセラレータなど) にわたって高度に最適化されたパフォーマンスを自動的に得ることができます。 さらに、Windows ML では、サポートされているすべてのハードウェアで一貫した動作が保証されます。

- **待ち時間が短く結果をリアルタイムで利用可能:** Windows デバイスの処理機能を使用して ML モデルを評価でき、画像やビデオなどの大きなデータ ボリュームをローカルでリアルタイムに分析できます。 分析結果は、ゲーム エンジンなどのパフォーマンスが集中するワークロードや、検索のインデックス作成などのバックグラウンド タスクですぐに効率的に使用できます。

- **柔軟性の向上:** Windows デバイス上で ML モデルをローカルに評価するオプションを使用すると、幅広いシナリオに対処できます。 たとえば ML モデルの評価を、デバイスがオフラインになっているときや、接続が断続的になったときに実行できます。 また、プライバシーやデータの主権の問題により、すべてのデータをクラウドに送信できないシナリオに対処することもできます。

- **運用コストの削減:** ML モデルは継続的な改善が必要な場合もあるため、ML モデルをクラウドでトレーニングし、Windows デバイスでローカルに評価すれば、最小限のデータのみがクラウドに送信されるため帯域幅コストが大幅に節約できます。 さらに、サーバー内に ML モデルを展開するシナリオでは、開発者は Windows ML ハードウェア アクセラレータを利用してモデル サービスを高速化することで、ワークロードを処理するために必要なマシンの数を減らすことができます。


## <a name="get-started"></a>開始 

トレーニング済みの ML モデルをアプリケーション コードに組み込むプロセスはシンプルで、次に示すいくつかの単純な手順のみが必要です。  

1. トレーニング済みの Open Neural Network Exchange (ONNX) モデルを取得するか、別の ML フレームワークでトレーニングされたモデルを [WinMLTools](convert-model-winmltools.md) で ONNX に変換します。

2. ONNX モデル ファイルをアプリケーションに追加します。または他の何らかの方法でターゲット デバイス上で使用できるようにします。

3. モデルをアプリケーション コードに統合し、アプリケーションをビルドして展開します。

![トレーニング環境, モデル参照の追加, アプリケーション, Windows ML](../images/winml-flow.png)

インボックス Windows ML から始めるには、「[Windows ML でモデルをアプリに統合する](integrate-model.md)」に進んでください。 [GitHub の Windows-Machine-Learning リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)にあるサンプル アプリを試すこともできます。

NuGet パッケージを使用する場合は、「[チュートリアル:既存の WinML アプリを NuGet パッケージに移植する](port-app-to-nuget.md)」を参照してください。

Windows ML の最新の機能と修正プログラムについては、「[リリース ノート](release-notes.md)」を参照してください。

## <a name="in-box-vs-nuget-winml-solutions"></a>インボックスと NuGet WinML ソリューションの比較

次の表は、Windows ML のインボックスおよび NuGet パッケージの可用性、配布、言語サポート、サービス、および上位互換性の側面を示しています。 

| | インボックス | NuGet |
| --- | --- | --- |
| 可用性 | Windows 10 バージョン 1809 以降 | Windows 8.1 以上 |
| 配布 | Windows SDK に組み込み | アプリケーションの一部としてパッケージ化して配布 |
| サービス | Microsoft 主導 (お客様は自動的にメリットを享受) | 開発者主導 |
| 上位互換性 | 新機能により自動的にロール フォワード | 開発者がパッケージを手動で更新する必要がある |


:::row:::
    :::column:::
    アプリケーションがインボックス ソリューションを使用して実行されている場合、Windows ML ランタイム (ONNX モデル推論エンジンを含む) は Windows 10 デバイス (またはサーバー展開を対象とする場合は Windows Server 2019) 上のトレーニング済みモデルを評価します。 Windows ML がハードウェア アブストラクションを処理するため、開発者は CPU や GPU、さらに将来は AI アクセラレータなどを含む広い範囲のシリコンを対象にすることができます。 Windows ML ハードウェア アクセラレータは [DirectML](https://docs.microsoft.com/windows/desktop/direct3d12/dml) 上に構築されます。これは ML 推論を実行するための高パフォーマンスで低レベルの API で、DirectX ファミリの一部です。 
    :::column-end:::
    :::column:::
        ![Windows ML のレイヤー](../images/overview-diagram.svg)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
    ![windows ml nuget パッケージ](../images/winml-nuget.svg)
    :::column-end:::
    :::column:::
    NuGet パッケージでは、次の図に示すように、これらのレイヤーはバイナリとして現れます。 Windows ML は、Microsoft.ai.machinelearning.dll に組み込まれています。 これには埋め込みの ONNX ランタイムが含まれていません。代わりに、ONNX ランタイムが onnxruntime.dll ファイルに組み込まれています。 WindowsAI NuGet パッケージに含まれるバージョンには、DirectML EP が埋め込まれています。 最後のバイナリである DirectML.dll は、DirectML としての実際のプラットフォーム コードであり、Windows に組み込まれている Direct 3D およびコンピューティングのドライバーの上に構築されています。 これら 3 つのバイナリはすべて NuGet リリースに含まれており、アプリケーションと共に配布することができます。 

    また、onnxruntime.dll に直接アクセスすると、クロスプラットフォームのシナリオを対象にすることができ、すべての Windows デバイスでスケーリングされるハードウェアに依存しないアクセラレータを一律に利用できます。 
    :::column-end:::
:::row-end:::

## <a name="other-machine-learning-solutions-from-microsoft"></a>Microsoft の他の機械学習ソリューション

Microsoft では、お客様のニーズに応じてさまざまな機械学習ソリューションを提供しています。 ソリューションはクラウド内で運用するものもあれば、オンプレミスやローカル デバイスで運用するものもあります。 詳細については、「[Microsoft の機械学習製品とは](https://docs.microsoft.com/azure/machine-learning/service/overview-more-machine-learning)」を参照してください。

[!INCLUDE [help](../includes/get-help.md)]
