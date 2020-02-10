---
author: rosanevallim
title: FAQ (よく寄せられる質問)
description: このページには、コミュニティからの最も一般的な質問への回答が含まれています。
ms.author: rovalli
ms.date: 7/2/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 0067de7380560337feb06186ff28ba431b167c93
ms.sourcegitcommit: 24d50c2813c16d5632c52c9dc6799afc6e52f8ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523622"
---
# <a name="faq-frequently-asked-questions"></a>FAQ (よく寄せられる質問)

このページには、コミュニティからの最も一般的な質問への回答が含まれています。

## <a name="how-do-i-know-if-the-onnx-model-i-have-will-run-with-windows-ml"></a>保有している ONNX モデルが Windows ML で動作するかどうかを確認するにはどうすればよいですか?

モデルが Windows ML で動作するかどうかを確認する最も簡単な方法としては、[WinML Model Runner ツール](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Tools/WinMLRunner)を使用します。 あるいは、「[ONNX バージョンと Windows ビルド](onnx-versions.md)」で、特定の Windows リリースでサポートされているすべての ONNX バージョンの詳細を確認することもできます。

## <a name="how-do-i-convert-a-model-of-a-different-format-to-onnx"></a>異なる形式のモデルを ONNX に変換するにはどうすればよいですか?

[WinMLTools](convert-model-winmltools.md) を使用すると、Apple CoreML や scikit-learn などのいくつかの異なる形式のモデルを ONNX に変換できます。

## <a name="i-am-getting-errors-when-trying-to-export-andor-convert-my-model-to-onnx-that-say-my-model-has-unsupported-operators-what-should-i-do"></a>モデルを ONNX にエクスポートまたは変換しようとすると、そのモデルに "サポートされていない演算子" が含まれているというエラーが表示されます。 どうすればよいですか?

ネイティブなトレーニング フレームワーク内の一部の演算子が現在、ONNX バージョンでサポートされていない可能性があります。 最初に、[対象の Windows ビルドでサポートされている ONNX バージョン](onnx-versions.md)を確認してから、サポートされている最大バージョンにモデルを変換してみることをお勧めします。 最新のバージョンの ONNX には、以前のバージョンと比較して、より多くの演算子に対するサポートが含まれています。

依然として問題が発生する場合は、データ サイエンス チームと協力して、サポートされていない演算子の使用を回避してみることをお勧めします。 お勧めするアプローチの 1 つとして、ソース フレームワーク内のモデルのアーキテクチャを変更し、モデルを対象の ONNX バージョンに変換またはエクスポートしてみる方法があります。 アーキテクチャの変換は、モデルを再トレーニングしなくても試みることができることに注意してください。そして、成功した場合は、モデルの完全な再トレーニングに進むことができます。

## <a name="why-cant-i-load-a-model"></a>モデルを読み込めないのはなぜですか?

モデルの読み込みでトラブルが発生する原因はいくつかありますが、UWP 上で開発している場合の最も一般的な原因の 1 つにファイルのアクセス制限があります。 既定では、UWP アプリケーションはファイル システムの特定の部分にしかアクセスできず、他の場所にアクセスするにはユーザーのアクセス許可または追加機能が必要になります。 詳細については、「[ファイル アクセス許可](https://docs.microsoft.com/windows/uwp/files/file-access-permissions)」を参照してください。

## <a name="which-version-of-winmltools-should-i-use"></a>どのバージョンの WinMLTools を使用すべきですか?

常に最新バージョンの **winmltools** パッケージをダウンロードしてインストールすることをお勧めします。 これにより、最新バージョンの Windows を対象とする ONNX モデルを確実に作成できるようになります。

## <a name="can-i-use-onnxmltools-instead-of-winmltools"></a>winmltools の代わりに onnxmltools を使用できますか?

はい。それは可能ですが、Windows ML でサポートされている最小の ONNX バージョンである ONNX v1.2.2 を対象とするには、適切なバージョンの [onnxmltools](https://github.com/onnx/onnxmltools) をインストールするようにする必要があります。 どのバージョンをインストールするかに関して確信がない場合は、最新バージョンの **winmltools** をインストールすることをお勧めします。 これにより、Windows でサポートされている ONNX バージョンが確実に対象になります。

## <a name="which-version-of-visual-studio-should-i-use-in-order-to-get-automatic-code-generation-mlgen"></a>自動コード生成 (mlgen) を実現するには、どのバージョンの Visual Studio を使用すべきですか?

[mlgen](mlgen.md) をサポートしている [Visual Studio](https://visualstudio.microsoft.com/vs/) の推奨される最小バージョンは 15.8.7 です。 Windows 10 バージョン 1903 以降では、**mlgen** が SDK に含まれなくなったため、拡張機能をダウンロードしてインストールする必要があります。 [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) と [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2) 向けにそれぞれ 1 つあります。

## <a name="i-get-an-error-message-when-trying-to-run-mlgen-and-no-code-is-generated-what-could-possibly-be-happening"></a>mlgen を実行しようとすると、エラー メッセージが表示され、コードが生成されません。 何が発生していると考えられるでしょうか?

mlgen を実行しようとしたときの最も一般的な 2 つのエラーは次のとおりです。

* **必要な属性 'consumed_inputs' が見つかりません**:このエラー メッセージが表示された場合、最も可能性が高いのは、17763 より古いバージョンの Windows 10 SDK で ONNX v1.2 モデルを実行しようとしていることです。SDK のバージョンを確認し、それをバージョン 17763 以降に更新することをお勧めします。
* **型エラー: ノード (ZipMap) の出力引数 (loss) の型 (map(string,tensor(float))) が予期された型と一致しません...** : このエラーが表示された場合、最も可能性が高いのは、ONNX モデルが WinML で受け入れられるビルド 17763 以降のバージョンより古いことです。 コンバーター パッケージを使用可能な最新バージョンに更新し、モデルを 1.2 バージョンの ONNX に再変換することをお勧めします。

## <a name="what-does-winml-run-on-by-default"></a>WinML は、既定ではどのデバイスで実行されますか?

[LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind) で実行するデバイスを指定しない場合や、**LearningModelDeviceKind.Default** を使用した場合は、どのデバイスでモデルを評価するかがシステムで決定されます。 通常、これは CPU です。 WinML を GPU で実行するようにするには、[LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice) を作成するときに次の値のいずれかを指定します。

* **LearningModelDeviceKind.DirectX**
* **LearningModelDeviceKind.DirectXHighPerformance**
* **LearningModelDeviceKind.DirectXMinPower**

[!INCLUDE [help](../includes/get-help.md)]
