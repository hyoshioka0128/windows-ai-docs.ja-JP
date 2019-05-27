---
author: rosanevallim
title: Visual Studio で Windows ML のモデルをトレーニングする方法
description: このステップ バイ ステップ チュートリアルでは、Visual Studio Tools for AI を使って Windows ML のモデルをトレーニングする方法について説明します。
ms.author: rovalli
ms.date: 4/2/2019
ms.topic: article
keywords: Windows 10, UWP, Windows Machine Learning, Visual Studio
ms.localizationpriority: medium
ms.openlocfilehash: 27c2fb2cdce9d19c6219c40f885ad9d720029f12
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179964"
---
# <a name="train-a-model-with-cntk"></a>Cntk モデルをトレーニングします。

このチュートリアルで使用します[Visual Studio Tools for AI](http://aka.ms/vstoolsforai)、ビルド、テスト、およびモデルをトレーニングするディープ ラーニングと AI ソリューションの配置用の拡張機能を開発します。 <!--for the MNIST sample app in [Get Started (UWP)](get-started-uwp.md)-->

モデルのトレーニングには、[Microsoft Cognitive Toolkit (CNTK)](http://www.microsoft.com/en-us/cognitive-toolkit) フレームワークと [MNIST データセット](http://yann.lecun.com/exdb/mnist/)を使います。データセットには、60,000 件の例から成るトレーニング セットと、10,000 件の手書きの数字の例から成るテスト セットが含まれています。 その後、モデルを [Open Neural Network Exchange (ONNX)](https://onnx.ai/) 形式で保存して、Windows ML で使用できるようにします。

## <a name="prerequisites"></a>前提条件
### <a name="install-visual-studio-tools-for-ai"></a>Visual Studio Tools for AI のインストール
最初に、[Visual Studio](https://www.visualstudio.com/downloads/) をダウンロードしてインストールする必要があります。 Visual Studio を開いたら、**Visual Studio Tools for AI** 拡張機能をアクティブ化します。

1. Visual Studio のメニュー バーをクリックし、[拡張機能と更新プログラム] を選択します。
2. [オンライン] タブをクリックし、[Visual Studio Marketplace の検索] を選択します。
3. 「Visual Studio Tools for AI」を検索します。 
3. **[ダウンロード]** ボタンをクリックします。 
4. インストールの完了後、Visual Studio を再起動します。 

Visual Studio を再起動すると、拡張機能がアクティブになります。 問題が発生した場合は、「[Visual Studio 拡張機能の検索と使用](h https://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions)」をご覧ください。

### <a name="download-sample-code"></a>サンプル コードのダウンロード
GitHub で、[Samples for AI](https://github.com/Microsoft/samples-for-ai) のリポジトリをダウンロードします。 これらのサンプルでは、TensorFlow、CNTK、Theano などでディープ ラーニングを始める方法がカバーされています。

### <a name="install-cntk"></a>CNTK のインストール
[CNTK for Python on Windows](https://docs.microsoft.com/en-us/cognitive-toolkit/setup-windows-python?tabs=cntkpy24) をインストールします。 Python がまだインストールされていない場合は、Python もインストールする必要があります。

または、ディープ ラーニング モデルの開発用にコンピューターを準備する方法として、[開発環境の準備に関するドキュメント](https://github.com/Microsoft/samples-for-ai/blob/master/README.md)には、Python、CNTK、TensorFlow、NVIDIA GPU ドライバー (オプション) などを簡単にインストールできるインストーラーが紹介されています。

## <a name="1-open-project"></a>1. プロジェクトを開く

Visual Studio を起動し、**[ファイル]、[開く]、[プロジェクト/ソリューション]** の順にクリックします。 Samples for AI のリポジトリから、**examples\cntk\python** フォルダーを選択し、**CNTKPythonExamples.sln** ファイルを開きます。

![ソリューションを開く](../images/open-solution.png)

## <a name="2-train-the-model"></a>2. モデルをトレーニングします。

MNIST プロジェクトをスタートアップ プロジェクトとして設定します。そのためには、python プロジェクトを右クリックし、**[スタートアップ プロジェクトに設定]** を選択します。

![ソリューションを開く](../images/mnist-startup.png)

次に、train_mnist_onnx.py ファイルを開くと**実行**キーを押してプロジェクト**f5 キーを押して**または緑の**実行**ボタン。

## <a name="3-view-the-model-and-add-it-to-your-app"></a>3.モデルを表示し、アプリに追加します。

ここで、トレーニング済みの **mnist.onnx** モデル ファイルが samples-for-ai/examples/cntk/python/MNIST フォルダーにあるはずです。 <!--You can use this trained **mnist.onnx** model file to build the MNIST sample app in [Get Started (UWP)](get-started-uwp.md)!-->

## <a name="4-learn-more"></a>4。詳細
[Azure GPU Virtual Machines](https://docs.microsoft.com/en-us/visualstudio/ai/tensorflow-vm) などを使ってディープ ラーニング モデルのトレーニングを高速化する方法については、[Microsoft の人工知能](https://www.microsoft.com/ai)と [Microsoft Machine Learning テクノロジ](https://docs.microsoft.com/en-us/azure/machine-learning/#other-microsoft-machine-learning-technologies)に関するページをご覧ください。

[!INCLUDE [help](../includes/get-help.md)]
