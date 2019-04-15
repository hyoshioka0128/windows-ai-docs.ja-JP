---
author: rosanevallim
title: FAQ (よく寄せられる質問)
description: このページには、コミュニティからの最も一般的な質問に対する回答が含まれています。
ms.author: rovalli
ms.date: 2/12/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: 4d0aab37ee9020ae29502653cf867ac673199f96
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474469"
---
# <a name="faq-frequently-asked-questions"></a>FAQ (よく寄せられる質問)

このページには、コミュニティからの最も一般的な質問に対する回答が含まれています。

## <a name="how-do-i-know-if-the-onnx-model-i-have-will-run-with-windows-ml"></a>ML の Windows で実行されますがある ONNX モデルかを確認する方法

Windows の ML API によってサポートされる最小 ONNX バージョン 1.2.2 です。 モデルをトレーニングするとき、1.2.2 にモデルを保存して、フレームワークがサポートしているかを確認形式。

## <a name="how-do-i-convert-a-model-of-a-different-format-to-onnx"></a>ONNX を別の形式のモデルを変換する方法

使用することができます[WinMLTools](convert-model-winmltools.md) Apple CoreML と scikit など、いくつかの異なる形式のモデルに変換する-ONNX する方法を説明します。

## <a name="which-version-of-winmltools-should-i-use"></a>WinMLTools のバージョンを使用する必要がありますか。

常にお勧めをダウンロードし、最新バージョンのインストール、 **winmltools**パッケージ。 Windows の最新バージョンを対象とする ONNX モデルを作成するようになります。

## <a name="can-i-use-onnxmltools-instead-of-winmltools"></a>Winmltools ではなく onnxmltools を使用できますか。

はい、できますが、その正しいバージョンをインストールするかどうかを確認する必要があります[onnxmltools](https://github.com/onnx/onnxmltools) ONNX v1.2.2 は、Windows の ML でサポートされている最小 ONNX バージョンを対象にするためです。 最新バージョンのインストールをお勧めをインストールするバージョンが不明な場合は、 **winmltools**代わりにします。 これにより、Windows でサポートされている ONNX バージョンを対象とすることができますが保証されます。

## <a name="which-version-of-visual-studio-should-i-use-in-order-to-get-automatic-code-generation-mlgen"></a>どのバージョンの Visual Studio 自動コード生成 (mlgen) を取得するために使用する必要がありますか。

最低限のバージョンをお勧めします[Visual Studio](https://visualstudio.microsoft.com/vs/)対応の[mlgen](mlgen.md) 15.8.7 です。 Windows 10、バージョンが 1903 以降で**mlgen**は不要になった SDK では、含まれるので、ダウンロードして、拡張機能をインストールする必要があります。 1 つ[Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)とに 1 つずつ[Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)します。

## <a name="i-get-an-error-message-when-trying-to-run-mlgen-and-no-code-is-generated-what-could-possibly-be-happening"></a>エラー メッセージが表示されるが生成される mlgen となしのコードを実行しようとしています。 場合によってどうしてでしょうか。

Mlgen を実行しようとするときは、2 つの最も一般的なエラーは次のとおりです。

* **必須属性 'consumed_inputs' がありません**:このエラー メッセージに発生した場合、ほとんどの場合はしようとして 17763; より古い Windows 10 SDK のバージョンで、ONNX v1.2 モデルを実行SDK のバージョンを確認して 17763 またはそれ以降のバージョンに更新をお勧めします。
* **型エラー:型 (map(string,tensor(float))) ノード (ZipMap) の出力引数 (損失) の種類に一致しません、予想される.**:このエラーが発生した場合、ほとんどの場合、ONNX モデルは 1 以降でビルド 17763 WinML で受け入れられるよりも古いバージョンです。 コンバーター パッケージを最新のバージョンに更新し、モデルの ONNX バージョン 1.2 に再変換することをお勧めします。

## <a name="why-cant-i-load-a-model"></a>モデルを読み込むことはできませんはなぜですか。

なぜ、モデルの読み込みに問題がある可能性がありますが、UWP で開発する場合は、最も一般的なものの 1 つはファイル アクセス制限のためのいくつかの理由があります。 既定では、UWP アプリケーションがのみ、ファイル システムの特定の部分へのアクセスし、ユーザー権限、またはその他の場所にアクセスするために余分な機能に必要なことができます。 参照してください[ファイル アクセス許可](https://docs.microsoft.com/windows/uwp/files/file-access-permissions)詳細についてはします。

## <a name="what-does-winml-run-on-by-default"></a>何が WinML 既定で実行しますか。

実行するデバイスを指定しないかどうかは[LearningModelDeviceKind](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevicekind)を使用する場合または**LearningModelDeviceKind.Default**システムはモデルを評価するデバイスを決定します。 これは、通常は CPU です。 GPU 上で WinML を実行するためには、作成するときに、次のいずれかの値を指定、 [LearningModelDevice](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodeldevice):

* **LearningModelDeviceKind.DirectX**
* **LearningModelDeviceKind.DirectXHighPerformance**
* **LearningModelDeviceKind.DirectXMinPower**

[!INCLUDE [help](includes/get-help.md)]