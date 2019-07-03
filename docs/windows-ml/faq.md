---
author: rosanevallim
title: FAQ (よく寄せられる質問)
description: このページには、コミュニティからの最も一般的な質問に対する回答が含まれています。
ms.author: rovalli
ms.date: 7/2/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 0067de7380560337feb06186ff28ba431b167c93
ms.sourcegitcommit: 24d50c2813c16d5632c52c9dc6799afc6e52f8ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523622"
---
# <a name="faq-frequently-asked-questions"></a>FAQ (よく寄せられる質問)

このページには、コミュニティからの最も一般的な質問に対する回答が含まれています。

## <a name="how-do-i-know-if-the-onnx-model-i-have-will-run-with-windows-ml"></a>ML の Windows で実行されますがある ONNX モデルかを確認する方法

Windows ML を使用したかどうかに、モデルは実行を確認する最も簡単な方法を使用して、[モデル ランナーを WinML ツール](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner)します。 または、チェック[ONNX バージョンと Windows ビルド](onnx-versions.md)サポートされている特定の Windows リリースの ONNX バージョンのすべての詳細についてはします。

## <a name="how-do-i-convert-a-model-of-a-different-format-to-onnx"></a>ONNX を別の形式のモデルを変換する方法

使用することができます[WinMLTools](convert-model-winmltools.md) Apple CoreML と scikit など、いくつかの異なる形式のモデルに変換する-ONNX する方法を説明します。

## <a name="i-am-getting-errors-when-trying-to-export-andor-convert-my-model-to-onnx-that-say-my-model-has-unsupported-operators-what-should-i-do"></a>エクスポートや ONNX モデルという私のモデルに変換しようとしています。 は「サポートされていない演算子です」ときにエラーが発生しました どうしたらいいでしょう。

ONNX バージョンでネイティブ トレーニング フレームワークのいくつかの演算子が現在サポートされていない可能性があります。 最初に、サポートされている確認してください[ONNX バージョン、ターゲットの Windows ビルド](onnx-versions.md)、最大のサポートされているバージョン、モデルに変換しようとします。 ONNX の以降のバージョンには、大規模な一連の以前のバージョンと比較演算子のサポートが含まれます。

問題が発生する場合は、サポートされていない演算子を回避する、データ サイエンス チームと連携お勧めします。 ソースのフレームワークで、モデルのアーキテクチャを変更し、変換/エクスポートの対象の ONNX バージョンへのモデルをお勧めの方法の 1 つです。 まだ、モデルを再トレーニングする必要があることに注意してください&mdash;アーキテクチャを変換しようとすることができ、成功した場合、移動できます、モデルの完全な再トレーニングします。

## <a name="why-cant-i-load-a-model"></a>モデルを読み込むことはできませんはなぜですか。

なぜ、モデルの読み込みに問題がある可能性がありますが、UWP で開発する場合は、最も一般的なものの 1 つはファイル アクセス制限のためのいくつかの理由があります。 既定では、UWP アプリケーションがのみ、ファイル システムの特定の部分へのアクセスし、ユーザー権限、またはその他の場所にアクセスするために余分な機能に必要なことができます。 参照してください[ファイル アクセス許可](https://docs.microsoft.com/windows/uwp/files/file-access-permissions)詳細についてはします。

## <a name="which-version-of-winmltools-should-i-use"></a>WinMLTools のバージョンを使用する必要がありますか。

常にお勧めをダウンロードし、最新バージョンのインストール、 **winmltools**パッケージ。 Windows の最新バージョンを対象とする ONNX モデルを作成するようになります。

## <a name="can-i-use-onnxmltools-instead-of-winmltools"></a>Winmltools ではなく onnxmltools を使用できますか。

はい、できますが、その正しいバージョンをインストールするかどうかを確認する必要があります[onnxmltools](https://github.com/onnx/onnxmltools) ONNX v1.2.2 は、Windows の ML でサポートされている最小 ONNX バージョンを対象にするためです。 最新バージョンのインストールをお勧めをインストールするバージョンが不明な場合は、 **winmltools**代わりにします。 これにより、Windows でサポートされている ONNX バージョンを対象とすることができますが保証されます。

## <a name="which-version-of-visual-studio-should-i-use-in-order-to-get-automatic-code-generation-mlgen"></a>どのバージョンの Visual Studio 自動コード生成 (mlgen) を取得するために使用する必要がありますか。

最低限のバージョンをお勧めします[Visual Studio](https://visualstudio.microsoft.com/vs/)対応の[mlgen](mlgen.md) 15.8.7 です。 Windows 10、バージョンが 1903 以降で**mlgen**は不要になった SDK では、含まれるので、ダウンロードして、拡張機能をインストールする必要があります。 1 つ[Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)とに 1 つずつ[Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)します。

## <a name="i-get-an-error-message-when-trying-to-run-mlgen-and-no-code-is-generated-what-could-possibly-be-happening"></a>エラー メッセージが表示されるが生成される mlgen となしのコードを実行しようとしています。 場合によってどうしてでしょうか。

Mlgen を実行しようとするときは、2 つの最も一般的なエラーは次のとおりです。

* **必須属性 'consumed_inputs' がありません**:このエラー メッセージに発生した場合、ほとんどの場合はしようとして 17763; より古い Windows 10 SDK のバージョンで、ONNX v1.2 モデルを実行SDK のバージョンを確認して 17763 またはそれ以降のバージョンに更新をお勧めします。
* **型エラー:型 (map(string,tensor(float))) ノード (ZipMap) の出力引数 (損失) の種類に一致しません、予想される.** :このエラーが発生した場合、ほとんどの場合、ONNX モデルは 1 以降でビルド 17763 WinML で受け入れられるよりも古いバージョンです。 コンバーター パッケージを最新のバージョンに更新し、モデルの ONNX バージョン 1.2 に再変換することをお勧めします。

## <a name="what-does-winml-run-on-by-default"></a>何が WinML 既定で実行しますか。

実行するデバイスを指定しないかどうかは[LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind)を使用する場合または**LearningModelDeviceKind.Default**システムはモデルを評価するデバイスを決定します。 これは、通常は CPU です。 GPU 上で WinML を実行するためには、作成するときに、次のいずれかの値を指定、 [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice):

* **LearningModelDeviceKind.DirectX**
* **LearningModelDeviceKind.DirectXHighPerformance**
* **LearningModelDeviceKind.DirectXMinPower**

[!INCLUDE [help](../includes/get-help.md)]
