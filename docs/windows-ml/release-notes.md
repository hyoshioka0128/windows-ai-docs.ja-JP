---
author: rosanevallim
title: リリース ノート
description: Windows の AI プラットフォームで最新の更新プログラム。
ms.author: rovalli
ms.date: 4/18/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: e306d8d1af0a421b8da7814f212483d3f7870fa9
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180034"
---
# <a name="release-notes"></a>リリース ノート

このページのレコードの更新 Windows ML、Windows 10 SDK の最新のビルドに。

## <a name="build-18362-windows-10-version-1903"></a>18362 (Windows 10、バージョンが 1903) のビルドします。

すべての機能と以前のビルドを flighted から更新プログラム:

* ONNX 1.3 のサポート
* 量子化の重みのトレーニング後を使用してモデル サイズの縮小をサポートします。 Int8 まで、モデルの重みをパックするのに WinMLTools の最新バージョンを使用することができます。
* Windows 10 SDK から mlgen の削除&mdash;代わりに次の Visual Studio 拡張機能のいずれか。
    * Visual Studio 2017 の場合:[Windows の Machine Learning の VS 2017 のコード ジェネレーター](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019:[Windows Machine Learning のコード ジェネレーター](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18829"></a>ビルド 18829

* [mlgen](mlgen.md) Windows 10 SDK から削除されました。 代わりに、いずれかのバージョンに応じて次の Visual Studio 拡張機能をインストールします。
    * Visual Studio 2017 の場合:[Windows の Machine Learning の VS 2017 のコード ジェネレーター](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)
    * Visual Studio 2019:[Windows Machine Learning のコード ジェネレーター](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)

## <a name="build-18290"></a>ビルド 18290
- 最小のサポートされている ONNX バージョン 1.2.2 (opset 7) を =
- 最大のサポートされている ONNX バージョン 1.3 (opset 8) を =
- サポートは、量子化の重みのトレーニング後を使用してサイズの縮小をモデルします。 Int8 まで、モデルの重みをパックするのに WinMLTools の最新バージョンを使用することができます。

## <a name="build-17763-windows-10-version-1809"></a>17763 (Windows 10、バージョンは 1809) のビルドします。

* Windows Machine Learning の最初の公式リリースします。
* ONNX 必要があります[v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2)します。
* [名前空間の Windows.AI.MachineLearning.Preview](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.preview)推奨[Windows.AI.MachineLearning 名前空間](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)します。

### <a name="known-issues"></a>既知の問題

* モデルのシーケンスを含む、MLGen が生成されます、 **IList&lt;ディクショナリ&lt;*キー*、*値*&gt; &gt;** 適切なのではなく**IList&lt;IDictionary&lt;*キー*、*値*&gt;&gt;** に市場をリードします。空の結果。 この問題を解決する適切な単に自動的に生成されたコードに置き換えます**IList&lt;IDictionary&lt;*キー*、*値*&gt;&gt;** 代わりにします。

## <a name="build-17723"></a>ビルド 17723

- ONNX 必要があります[v1.2](https://github.com/onnx/onnx/tree/rel-1.2.2)します。
- GPU ベースのモデル推論 F16 データ型をサポートしている[より高いパフォーマンス](performance-memory.md)モデル フット プリントが縮小します。 WinMLTools を使用する[FP16 FP32 から、モデルに変換](convert-model-winmltools.md#convert-to-floating-point-16)します。
- 使用するデスクトップ アプリに許可[Windows.AI.MachineLearning Api](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)で[WinRT/C++](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)します。

[!INCLUDE [help](../includes/get-help.md)]
