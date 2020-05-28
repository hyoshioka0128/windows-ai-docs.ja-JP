---
author: rosanevallim
title: リリース ノート
description: Windows AI プラットフォームについての最新情報。
ms.author: rovalli
ms.date: 5/19/2020
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 86ce0f25fcac48a8f1e9983fc986f3db61f93be4
ms.sourcegitcommit: f41fad7e6b6280bbbaf4157703f03fb7f23de676
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631817"
---
# <a name="release-notes"></a>リリース ノート

このページには、Windows 10 SDK の最新のビルドにおける Windows ML に関する最新情報を記載しています。


## <a name="windows-ml-nuget-package---may-2020-version"></a>Windows ML NuGet パッケージ - 2020 月 5 月バージョン 

- [ONNX ランタイム 1.3 上に構築](https://github.com/microsoft/onnxruntime/blob/master/docs/HighLevelDesign.md#the-onnx-runtime-and-windows-os-integration)
- MachineLearningContract v3 に対応 
- ONNX 1.6 および opset 11 のサポート 
- CPU の実行は、Windows 8.1 までサポートされています。GPU の実行は、Windows 10 バージョン 1709 までサポートされています 
- 認定されている既知のテスト済みのパスは、C++ を使用するデスクトップ アプリケーションです。 ストア アプリケーションと Windows アプリケーション認定キットは、まだサポートされていません。 

## <a name="build-19041-windows-10-version-2004"></a>ビルド 19041 (Windows 10 バージョン 2004)

ONNX 1.4 および opset 9 (CPU および GPU) のサポート 

API Surface の追加:
* [CloseModelOnSessionCreation](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsessionoptions.closemodelonsessioncreation?view=winrt-19041): 作業メモリを削減するために構成する新しい **LearningModelSessionOptions** パラメーターです。

ツール:

* WinMLTools コンバーターは新しい ONNX バージョンと opset をサポート  
* 新しいパフォーマンス メトリックを公開する WinMLRunner への最適化 

## <a name="build-18362-windows-10-version-1903"></a>ビルド 18362 (Windows 10 バージョン 1903)

すべての機能と以前にフライト化されたビルドからの更新:

* ONNX 1.3 のサポート
* トレーニング後の重みの量子化によるモデル サイズの削減のサポート。 最新バージョンの WinMLTools を使用すると、モデルの重みを int8 に縮小できます。
* Windows 10 SDK から mlgen の削除&mdash;代わりに次のいずれかの Visual Studio 拡張機能を使用します。
    * Visual Studio 2017: [Windows Machine Learning コード ジェネレーター VS 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019: [Windows Machine Learning コード ジェネレーター](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18829"></a>ビルド 18829

* [mlgen](mlgen.md) は Windows 10 SDK から削除されました。 代わりに、お使いのバージョンに応じて、次のいずれかの Visual Studio 拡張機能をインストールします。
    * Visual Studio 2017: [Windows Machine Learning コード ジェネレーター VS 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019: [Windows Machine Learning コード ジェネレーター](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18290"></a>ビルド 18290
- サポートされている最小 ONNX バージョン = 1.2.2 (opset 7)
- サポートされている最大 ONNX バージョン = 1.3 (opset 8)
- トレーニング後の重みの量子化によるモデル サイズの削減のサポートします。 最新バージョンの WinMLTools を使用すると、モデルの重みを int8 に縮小できます。

## <a name="build-17763-windows-10-version-1809"></a>ビルド 17763 (Windows 10 バージョン 1809)

* Windows Machine Learning の最初の公式リリース。
* ONNX [v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2) が必要です。
* [Windows.AI.MachineLearning.Preview 名前空間](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.preview)は非推奨になり、[Windows.AI.MachineLearning 名前空間](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)を代わりに使用します。

### <a name="known-issues"></a>既知の問題

* シーケンスを含むモデルの場合、MLGen で適正な **IList&lt;IDictionary&lt;*key*, *value*&gt;&gt;** ではなく、**IList&lt;Dictionary&lt;*key*, *value*&gt;&gt;** が生成され、結果が空になります。 この問題を解決するには、単に、自動生成されたコードを適正な **IList&lt;IDictionary&lt;*key*, *value*&gt;&gt;** に置き換えます。

## <a name="build-17723"></a>ビルド 17723

- ONNX [v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2) が必要です。
- [パフォーマンスの向上](performance-memory.md)とモデル フットプリントの削減のために、GPU ベースのモデル推論を使用した F16 データ型をサポートします。 WinMLTools を使用して、[モデルを FP32 から FP16 に変換](convert-model-winmltools.md#convert-to-floating-point-16)できます。
- デスクトップ アプリで [WinRT/C++](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/) を用いて [Windows.AI.MachineLearning API](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) を使用できます。

[!INCLUDE [help](../includes/get-help.md)]
