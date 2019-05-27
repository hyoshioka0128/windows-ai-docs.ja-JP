---
author: eliotcowley
title: ツールとサンプル
description: Windows Machine Learning 用には、さまざまなツールと使用可能なサンプルについて説明します。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows の機械学習、WinML、サンプル、ツール
ms.localizationpriority: medium
ms.openlocfilehash: d305184d493549c7d2f9ed126975f3310d4e1279
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179954"
---
# <a name="tools-and-samples"></a>ツールとサンプル

[GitHub 上の Windows 機械学習リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)モデルを確認し、開発中に問題のトラブルシューティングに役立つツールと同様に、Windows Machine Learning を使用する方法を示すサンプル アプリケーションが含まれています。

## <a name="tools"></a>ツール

次のツールは、GitHub で入手できます。

| 名前 | 説明 |
|------|-------------|
| [コード ジェネレーターの WinML (mlgen)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) | 役立つ Visual Studio 拡張機能は、UWP プロジェクトにトレーニング済みの ONNX ファイルを追加すると、テンプレート コードを生成することによって、UWP アプリで WinML Api を使用して開始します。 使用可能な[Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)と[2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2)します。 参照してください、[ドキュメント](mlgen.md)詳細についてはします。
| [WinML ダッシュ ボード (プレビュー)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) | 表示、編集、変換、および Windows ML の推論エンジンの機械学習モデルの検証の GUI ベースのツールです。 |
| [WinMLRunner](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner) | コマンド ライン ツールには、入力と出力の変数が tensors またはイメージを .onnx または .pb モデルを実行できます。 モデルに対する WinML Api を実行し、アプリケーションに統合する前に問題がヒットしたかどうかを確認することができるので便利です。 |
| [WinMLTools](https://pypi.org/project/winmltools/) | さまざまな ML ツールキットから ONNX、だけでなく、量子化ツール、モデルのメモリ フット プリントを削減へのモデル変換を提供する Python パッケージです。 |

## <a name="samples"></a>サンプル

次のサンプル アプリケーションは、GitHub で入手できます。

| 名前 | 説明 |
|------|-------------|
| [AdapterSelection (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/AdapterSelection/AdapterSelection/cpp) | デスクトップ アプリケーションをモデルを実行するため、アダプターを特定のデバイスを選択する方法を示します。 |
| [カスタム演算子のサンプル (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomOperatorCPU/desktop/cpp) | デスクトップ アプリケーションを複数のカスタム CPU 演算子を定義します。 これらの 1 つは、独自のワークフローに統合できるデバッグ演算子です。 |
| [カスタム Tensorization (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) | CPU と GPU の両方で WinML Api を使用して、入力の画像を tensorize する方法を示します。 |
| [Custom Vision (UWP C#)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) | カスタムのビジョンを使用して、クラウドに ONNX モデルをトレーニングして、WinML をアプリケーションに統合する方法を示します。 |
| [Emoji8 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs) | WinML を使用すると、電源を楽しめる方法を示しています。 アプリケーションの感情を検出します。 |
| [FNS 転送のスタイル設定 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer) | スタイルを変更する画像またはビデオ ストリームを FNS キャンディ スタイル転送モデルを使用します。 |
| [MNIST (UWP C#/C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST) | 対応する[チュートリアル。Windows Machine Learning の UWP アプリケーションの作成 (C#)](get-started-uwp.md)します。 基礎から開始や、チュートリアルで完成したプロジェクトを実行します。 |
| [PlaneIdentifier (UWP C#、WPF C#)](https://github.com/Microsoft/Windows-AppConsult-Samples-UWP/tree/master/PlaneIdentifier) | Azure では、特定のオブジェクトが特定のイメージに含まれているかどうかを検出するために、Custom Vision service を使用して生成された、事前トレーニング済みの機械学習モデルを使用して: 平面。 |
| [SqueezeNet オブジェクトの検出 (Win32 C++、UWP C#/JavaScript)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection) | SqueezeNet、事前トレーニング済みの機械学習モデルを使用して、ファイルからユーザーが選択した画像の主要なオブジェクトを検出します。 |
| [SqueezeNet オブジェクトの検出 (Azure IoT Edge on Windows、 C#)](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/EdgeModules/SqueezeNetObjectDetection/cs) | Windows で実行されている Azure IoT Edge モジュールで Windows ML 推論を実行する方法を示すサンプル モジュールです。 イメージは、SqueezeNet モデルに対する inferenced、接続されたカメラによって提供され、IoT Hub に送信します。 |
| [winml_tracker (ROS C++)](https://github.com/ms-iot/winml_tracker) | WinML を使用して、カメラのユーザー (またはその他のオブジェクト) を追跡する ROS (ロボット オペレーティング システム) ノードは、次のフレームです。 |

[!INCLUDE [help](../includes/get-help.md)]
