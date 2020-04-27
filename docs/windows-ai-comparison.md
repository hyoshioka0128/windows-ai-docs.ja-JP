---
title: Windows AI ソリューションを選択する
description: アプリケーションに適した Microsoft AI ソリューションの選択に関するサポートを受けてください。
author: mattwojo
ms.author: mattwoj
ms.date: 09/18/2019
ms.topic: article
keywords: Windows 10、Windows AI、Windows ML、WinML、Windows Machine Learning、Microsoft AI、比較する、比較、Windows Vision Skills、Direct ML
ms.localizationpriority: medium
ms.openlocfilehash: f78772f11bbe0697acc7c62b91df06b69b2c7312
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "74782645"
---
# <a name="which-ai-solution-is-right-for-me"></a>自分に適した AI ソリューション

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
