---
title: ツールとサンプル
description: Windows Machine Learning で使用できるさまざまなツールとサンプルについて説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10、Windows Machine Learning、WinML、サンプル、ツール
ms.localizationpriority: medium
ms.openlocfilehash: 453d43796e559a69591d4c8290b3acc5fb66f302
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70157967"
---
# <a name="tools-and-samples"></a>ツールとサンプル

[GitHub の Windows-Machine-Learning リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)には、Windows Machine Learning の使用方法を示すサンプル アプリケーションのほか、モデルの検証や開発中の問題のトラブルシューティングに役立つツールが含まれています。

## <a name="tools"></a>ツール

GitHub では、次のツールを入手できます。

| 名前 | 説明 |
|------|-------------|
| [WinML コード ジェネレーター (mlgen)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) | トレーニング済みの ONNX ファイルをユーザーが UWP プロジェクトに追加したときにテンプレート コードを生成することにより、UWP アプリで WinML API を使用開始するために役立つ Visual Studio 拡張機能。 [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) および [2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2) で使用できます。 詳細については、[ドキュメント](mlgen.md)を参照してください。
| [WinML ダッシュボード (プレビュー)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) | Windows ML の推論エンジンのための機械学習モデルを表示、編集、変換、および検証するための GUI ベースのツール。 |
| [WinMLRunner](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner) | 入力および出力変数がテンソルまたはイメージである .onnx または .pb モデルを実行できるコマンド ライン ツール。 モデルをアプリケーションに統合する前に、そのモデルに対して WinML API を実行し、何か問題が発生するかどうかを確認できる有用なツールです。 |
| [WinMLTools](https://pypi.org/project/winmltools/) | さまざまな ML ツールキットから ONNX へのモデルの変換や、モデルのメモリ占有領域を削減するための量子化ツールを提供する Python パッケージ。 |

## <a name="samples"></a>サンプル

GitHub では、次のサンプル アプリケーションを入手できます。

| 名前 | 説明 |
|------|-------------|
| [AdapterSelection (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/AdapterSelection/AdapterSelection/cpp) | モデルを実行するための特定のデバイス アダプターを選択する方法を示すデスクトップ アプリケーション。 |
| [カスタム演算子のサンプル (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomOperatorCPU/desktop/cpp) | 複数のカスタム CPU 演算子を定義するデスクトップ アプリケーション。 これらのうちの 1 つが、独自のワークフローに統合できるデバッグ演算子です。 |
| [カスタム テンソル化 (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) | CPU と GPU の両方で WinML API を使用して入力イメージをテンソル化する方法を示します。 |
| [Custom Vision (UWP C#)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) | Custom Vision を使用してクラウド内の ONNX モデルをトレーニングし、WinML を使用してそれをアプリケーションに統合する方法を示します。 |
| [Emoji8 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs) | WinML を使用して、楽しい感情を検出するアプリケーションを強化する方法を示します。 |
| [FNS スタイル トランスファー (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer) | FNS-Candy スタイル トランスファー モデルを使用して、イメージまたはビデオ ストリームのスタイルを再設定します。 |
| [MNIST (UWP C#/C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST) | 「[チュートリアル: Windows Machine Learning の UWP アプリケーションの作成 (C#)](get-started-uwp.md)」に対応します。 基礎から始めてチュートリアルを実行するか、または完成したプロジェクトを実行します。 |
| [PlaneIdentifier (UWP C#, WPF C#)](https://github.com/Microsoft/Windows-AppConsult-Samples-UWP/tree/master/PlaneIdentifier) | Azure の Custom Vision サービスを使用して生成された事前トレーニング済みの機械学習モデルを使用して、指定されたイメージに平面という特定のオブジェクトが含まれているかどうかを検出します。 |
| [SqueezeNet オブジェクト検出 (Win32 C++、UWP C#/JavaScript)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection) | 事前トレーニング済みの機械学習モデルである SqueezeNet を使用して、ファイルからユーザーによって選択されたイメージ内の主要なオブジェクトを検出します。 |
| [SqueezeNet オブジェクト検出 (Windows 上の Azure IoT Edge、C#)](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/EdgeModules/SqueezeNetObjectDetection/cs) | これは、Windows 上で実行されている Azure IoT Edge モジュールで Windows ML 推論を実行する方法を示すサンプル モジュールです。 イメージは接続されたカメラによって提供され、SqueezeNet モデルに対して推論された後、IoT Hub に送信されます。 |
| [winml_tracker (ROS C++)](https://github.com/ms-iot/winml_tracker) | WinML を使用してカメラ フレーム内の人物 (または他のオブジェクト) を追跡する ROS (Robot Operating System) ノード。 |

[!INCLUDE [help](../includes/get-help.md)]
