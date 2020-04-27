---
author: rosanevallim
title: mlgen を使ったコードの自動生成について
description: Windows ML のコード ジェネレーター mlgen は、アプリでモデルの読み込み、バインド、評価を簡単に行うことができるインターフェイス (C#、C++/WinRT、および C++/CX) を作成します。
ms.author: rovalli
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 7658b35a6bb19133380cf021a47d9c35ffc62a3b
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "66181894"
---
# <a name="automatic-code-generation-with-mlgen"></a>mlgen を使ったコードの自動生成について

<br/>

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

<br/>

Windows Machine Learning のコード ジェネレーター **mlgen** は、[Windows ML API](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning) を自動的に呼び出すラッパー クラスを含むインターフェイス (C#、[C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)、および C++/CX) を作成します。これにより、プロジェクトでモデルの読み込み、バインド、評価を簡単に行うことができます。

**mlgen** は、VS 2017 以降で WinML アプリケーションを作成する開発者向けの [Visual Studio](https://visualstudio.microsoft.com/downloads/) 拡張機能として提供されます。

Windows 10 バージョン 1903 以降では、**mlgen** が Windows 10 SDK に含まれなくなったため、拡張機能をダウンロードしてインストールする必要があります。 [Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen) と [Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2) 向けにそれぞれ 1 つあります。

**mlgen** をインストールし、Visual Studio プロジェクト内で ONNX ファイルをプロジェクトの **Assets** フォルダーに追加すると、VS が新しいインターフェイス ファイル内に Windows ML ラッパー クラスを生成します。 これらのクラスとメソッドを使用して、モデルをアプリケーションに統合できます。 この方法を使用してモデルを統合するチュートリアルについては、「[チュートリアル: Windows Machine Learning の UWP アプリケーションの作成 (C#)](get-started-uwp.md)」を参照してください。

[!INCLUDE [help](../includes/get-help.md)]
