---
title: 機械学習モデルとは
description: Windows Machine Learning のコンテキストにおけるモデルの概要について説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: a2c43090d44d6ac3c9e3c095ff83da5d58976265
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156267"
---
# <a name="what-is-a-machine-learning-model"></a>機械学習モデルとは

機械学習モデルとは、特定の種類のパターンを認識するようにトレーニングされたファイルのことです。 データのセットを使用してモデルをトレーニングし、それらのデータから推論し、学習するためにモデルが使用できるアルゴリズムをモデルに提供します。

モデルのトレーニングが完了したら、そのモデルを使用して、モデルがこれまで見たことのないデータから推論し、そのデータに関する予測を行うことができます。 たとえば、顔の表情に基づいてユーザーの感情を認識できるアプリケーションを構築するとします。 特定の感情にタグ付けされた複数の顔の画像をモデルに提供してモデルをトレーニングすることで、ユーザーの感情を認識できるアプリケーションでそのモデルを使用できるようになります。 このようなアプリケーションの例については、[Emoji8 のサンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs)を参照してください。

Windows Machine Learning では、[Open Neural Network Exchange (ONNX)](https://onnx.ai/) 形式をモデルとして使用します。 事前トレーニング済みのモデルをダウンロードすることも、独自のモデルをトレーニングすることもできます。 詳細については、[Windows ML 用の ONNX モデルを入手する](get-onnx-model.md)方法に関する記事を参照してください。

[!INCLUDE [help](../includes/get-help.md)]
