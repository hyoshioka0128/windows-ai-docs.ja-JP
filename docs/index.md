---
layout: LandingPage
author: eliotcowley
title: Windows AI
description: AI の能力を駆使して Windows アプリケーションを変革してください。
ms.author: elcowle
ms.date: 4/17/2019
ms.topic: landing-page
keywords: Windows 10、Windows AI
ms.localizationpriority: medium
ms.openlocfilehash: 9161d0494b64035385e46908a53aa81b8e107099
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175749"
---
# <a name="windows-ai"></a>Windows AI

人工知能の能力を駆使して Windows アプリケーションを変革してください。 Windows AI では、複雑な問題に対してインテリジェントなソリューションを提供することによって、お客様とビジネスを強化します。

<br/>

<div style="text-align:center">
    <img src="images/windows-ai-photo.png" alt="AI on farm"/>
</div>

<ul class="cardsK panelContent">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <a href="windows-ml/index.md">
                                <img src="https://docs.microsoft.com/media/hubs/windows/windows-ai.svg"
                                    alt="WinML graphic"
                                    data-linktype="external"
                                    class="x-hidden-focus"/>
                            </a>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>
                            <a href="windows-ml/index.md">Windows Machine Learning</a>
                        </h3>
                        <p>Windows アプリにトレーニング済みの機械学習モデルを統合する方法について説明します。</p>
                        <br/>
                        <ul>
                            <li><a href="windows-ml/get-started-uwp.md">チュートリアル: WinML UWP アプリを作成する (C#)</a></li>
                            <li><a href="windows-ml/what-is-a-machine-learning-model.md">機械学習モデルとは</a></li>
                            <li><a href="windows-ml/api-reference.md">WinML API リファレンス</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <a href="windows-vision-skills/index.md">
                                <img src="https://docs.microsoft.com/media/hubs/cortana/cortana-get-started-build-skill-language.svg" alt="Windows Vision Skills graphic" data-linktype="external" class="x-hidden-focus"/>
                            </a>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>
                            <a href="windows-vision-skills/index.md">Windows Vision Skills</a>
                        </h3>
                        <p>スキルを使用して、複雑なコンピューター ビジョンを抽象化します。</p>
                        <br/>
                        <ul>
                            <li><a href="windows-vision-skills/tutorial.md">チュートリアル: ビジョン スキルの作成 (C#)</a></li>
                            <li><a href="windows-vision-skills/tutorial1.md">チュートリアル: Windows Vision Skills の UWP アプリを作成する (C#)</a></li>
                            <li><a href="windows-vision-skills/important-api-concepts.md">重要な API の概念</a></li>
                            <li><a href="windows-vision-skills/samples.md">Windows Vision Skills のサンプル</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml">
                                <img src="https://docs.microsoft.com/media/hubs/cortana/cortana-resources-samples.svg" alt="DirectML graphic" data-linktype="external" class="x-hidden-focus"/>
                            </a>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>
                            <a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml">Direct Machine Learning (DirectML)</a>
                        </h3>
                        <p>低レベルの DirectX スタイルの API を使用して高パフォーマンスの機械学習を実装します。</p>
                        <br/>
                        <ul>
                            <li><a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml-intro">DirectML の概要</a></li>
                            <li><a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml-binding">DirectML のバインド</a></li>
                            <li><a href="https://docs.microsoft.com/windows/desktop/direct3d12/dml-min-app">DirectML のサンプル アプリケーション</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

## <a name="which-solution-is-right-for-me"></a>自分に適したソリューション

Microsoft ではいくつかの種類の AI ソリューションが提供されており、いくつかのオプションを自由に使用できます。 しかし、アプリケーションに対してどれを使用するかをどのようにして選べばよいのでしょうか。 詳しく見てみましょう。

### <a name="i-want-to-integrate-a-machine-learning-model-into-my-application-and-run-it-on-the-device-by-taking-full-advantage-of-hardware-acceleration"></a>機械学習モデルをアプリケーションに統合し、ハードウェア アクセラレータの利点を十分に利用することによってアプリケーションをデバイス上で実行したい

[Windows Machine Learning](windows-ml/index.md) が最適な選択肢です。 これらの高レベルな WinRT API は、Windows 10 アプリケーション (UWP、デスクトップ) 上で動作し、デバイス上でモデルを直接評価します。 パフォーマンス向上のために、デバイスの GPU (ある場合) を利用することもできます。

### <a name="i-want-to-integrate-computer-vision-into-my-application-and-take-advantage-of-platform-optimizations"></a>コンピューター ビジョンをアプリケーションに統合し、プラットフォームの最適化を活用したい

[Windows Vision Skills](windows-vision-skills/index.md) を選ぶべきです。 このシンプルなフレームワークを使用して、エッジ デバイスでハードウェア アクセラレータを利用するカスタム ビジョン アプリケーションを構築できます。 事前構築されたライブラリを組み合わせて、一般的な画像処理タスクと特殊タスク用の ML モデルを実現することができます。

### <a name="i-want-to-have-fuller-control-over-resource-utilization-during-model-execution-for-high-intensive-applications"></a>リソース集約型アプリケーションのモデルを実行中にリソース使用率をより完全に制御したい

[DirectML](https://docs.microsoft.com/windows/desktop/direct3d12/dml) を選ぶとよいでしょう。 これらの DirectX スタイルの API は、C++ のゲーム開発者が使い慣れたプログラミング パラダイムを提供し、ハードウェアの利点を最大限に活かすことができます。

### <a name="i-want-to-train-test-and-deploy-ml-models-with-a-framework-that-is-familiar-to-a-net-developer"></a>.NET 開発者が使い慣れたフレームワークを使用して、ML モデルをトレーニング、テスト、および展開したい

.NET 開発者向けに構築された機械学習フレームワークである [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) をお試しください。

### <a name="i-want-to-leverage-the-power-of-the-azure-cloud-for-training-and-deploying-ml-models"></a>ML モデルのトレーニングと展開のために Azure クラウドの能力を活用したい

Azure で実行される多くの製品とサービスを含む、Microsoft から入手できるソリューションの包括的な一覧は、「[Microsoft の機械学習製品とは](https://docs.microsoft.com/azure/architecture/data-guide/technology-choices/data-science-and-machine-learning)」を参照してください。
