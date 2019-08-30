---
title: ツールとサンプル
description: Windows Machine Learning で使用できるさまざまなツールとサンプルについて説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、サンプル、ツール
ms.localizationpriority: medium
ms.openlocfilehash: 453d43796e559a69591d4c8290b3acc5fb66f302
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157967"
---
# <a name="tools-and-samples"></a>ツールとサンプル

[GitHub の windows-Machine Learning リポジトリ](https://github.com/Microsoft/Windows-Machine-Learning)には、windows Machine Learning の使用方法を示すサンプルアプリケーションと、開発時のモデルの検証および問題のトラブルシューティングに役立つツールが含まれています。

## <a name="tools"></a>ツール

GitHub では、次のツールを使用できます。

| 名前 | 説明 |
|------|-------------|
| [WinML コードジェネレーター (mlgen)](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) | Uwp プロジェクトにトレーニング済みの ONNX ファイルを追加するときにテンプレートコードを生成することにより、UWP アプリで WinML Api の使用を開始するための Visual Studio 拡張機能。 [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)および[2019](https://marketplace.visualstudio.com/items?itemName=WinML.MLGenV2)で使用できます。 詳細については、[ドキュメント](mlgen.md)を参照してください。
| [WinML ダッシュボード (プレビュー)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLDashboard) | Windows ML の推定エンジンの機械学習モデルを表示、編集、変換、および検証するための GUI ベースのツール。 |
| [WinMLRunner](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner) | 入力変数と出力変数が tensors または image である onnx または pb モデルを実行できるコマンドラインツール。 モデルに対して WinML Api を実行して、アプリケーションに統合する前に問題が発生しているかどうかを確認できるため便利です。 |
| [WinMLTools](https://pypi.org/project/winmltools/) | さまざまな ML ツールキットから ONNX へのモデル変換、およびモデルのメモリフットプリントを減らすための量子化ツールを提供する Python パッケージ。 |

## <a name="samples"></a>サンプル

次のサンプルアプリケーションは、GitHub で入手できます。

| 名前 | 説明 |
|------|-------------|
| [AdapterSelection (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/AdapterSelection/AdapterSelection/cpp) | モデルを実行するために特定のデバイスアダプターを選択する方法を示すデスクトップアプリケーション。 |
| [カスタム演算子のサンプル ( C++Win32)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomOperatorCPU/desktop/cpp) | 複数のカスタム CPU 演算子を定義するデスクトップアプリケーション。 これらのうちの1つは、独自のワークフローに統合できる debug 操作です。 |
| [カスタムのカスタマイズ (Win32 C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/CustomTensorization) | CPU と GPU の両方で WinML Api を使用して入力イメージを管理する方法を示します。 |
| [Custom Vision (UWP C#)](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml) | Custom Vision を使用してクラウドで ONNX モデルをトレーニングし、WinML を使用してアプリケーションに統合する方法について説明します。 |
| [Emoji8 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs) | WinML を使用して、楽しい感情を検出するアプリケーションを強化する方法を示します。 |
| [FNS スタイル転送 (UWP C#)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/FNSCandyStyleTransfer) | では、画像またはビデオストリームのスタイルを変更するために、FNS のキャンディスタイルの転送モデルを使用します。 |
| [MNIST (UWP C#/C++)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/MNIST) | 次の[チュートリアルに対応します。Windows Machine Learning UWP アプリケーション (C#)](get-started-uwp.md)を作成します。 最初から開始してチュートリアルを実行するか、完成したプロジェクトを実行します。 |
| [PlaneIdentifier (UWP C#、WPF C#)](https://github.com/Microsoft/Windows-AppConsult-Samples-UWP/tree/master/PlaneIdentifier) | Azure 上の Custom Vision サービスを使用して生成されたトレーニング済みの機械学習モデルを使用して、特定のイメージに特定のオブジェクト (平面) が含まれているかどうかを検出します。 |
| [SqueezeNet オブジェクトの検出 ( C++Win32、 C#UWP、JavaScript)](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection) | 事前トレーニング済みの機械学習モデルである SqueezeNet を使用して、ユーザーがファイルから選択したイメージ内の主要なオブジェクトを検出します。 |
| [SqueezeNet オブジェクト検出 (Windows では Azure IoT Edge C#、)](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/EdgeModules/SqueezeNetObjectDetection/cs) | これは、windows で実行されている Azure IoT Edge モジュールで Windows ML 推論を実行する方法を示すサンプルモジュールです。 画像は、接続されたカメラによって提供され、SqueezeNet モデルに対して inferenced され、IoT Hub に送信されます。 |
| [winml_tracker (ROS C++)](https://github.com/ms-iot/winml_tracker) | ROS (ロボットオペレーティングシステム) ノード。 WinML を使用して、カメラフレーム内の people (またはその他のオブジェクト) を追跡します。 |

[!INCLUDE [help](../includes/get-help.md)]
