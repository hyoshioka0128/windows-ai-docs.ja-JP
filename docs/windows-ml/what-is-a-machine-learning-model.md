---
title: 機械学習モデルとは
description: Windows Machine Learning のコンテキストにおけるモデルの概要について説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: a2c43090d44d6ac3c9e3c095ff83da5d58976265
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156267"
---
# <a name="what-is-a-machine-learning-model"></a>機械学習モデルとは

機械学習モデルは、特定の種類のパターンを認識するようにトレーニングされたファイルです。 データのセットに対してモデルをトレーニングし、そのデータを理由と学習に使用できるアルゴリズムを提供します。

モデルのトレーニングが完了したら、それを使用して、以前に表示されていないデータを確認し、それらのデータに関する予測を行うことができます。 たとえば、顔式に基づいてユーザーの感情を認識できるアプリケーションを構築するとします。 モデルをトレーニングするには、それぞれが特定の感情にタグ付けされている顔の画像を提供します。その後、ユーザーの感情を認識できるアプリケーションでそのモデルを使用できます。 このようなアプリケーションの例については、 [Emoji8 サンプル](https://github.com/Microsoft/Windows-Machine-Learning/tree/master/Samples/Emoji8/UWP/cs)を参照してください。

Windows Machine Learning では、モデルに[Open ニューラル Network Exchange (ONNX)](https://onnx.ai/)形式が使用されます。 事前トレーニング済みのモデルをダウンロードすることも、独自のモデルをトレーニングすることもできます。 詳細については、「 [GET ONNX model For WINDOWS ML](get-onnx-model.md) 」を参照してください。

[!INCLUDE [help](../includes/get-help.md)]
