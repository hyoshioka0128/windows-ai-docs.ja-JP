---
author: rosanevallim
title: mlgen を使ったコードの自動生成について
description: Windows の ML のコード ジェネレーター mlgen インターフェイスを作成します (C#、 C++/WinRT、およびC++/CX) 簡単に読み込み、バインド、およびアプリでのモデルを評価することができます。
ms.author: rovalli
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 7658b35a6bb19133380cf021a47d9c35ffc62a3b
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181894"
---
# <a name="automatic-code-generation-with-mlgen"></a>mlgen を使ったコードの自動生成について

<br/>

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

<br/>

Windows Machine Learning のコード ジェネレーター **mlgen**インターフェイスを作成します (C#、 [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)、およびC++/CX) ラッパー クラスを呼び出し、 [Windows ML API](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)のバインド、およびプロジェクトでモデルを評価する、簡単に読み込むには、することができます。

**mlgen**として提供されて、 [Visual Studio](https://visualstudio.microsoft.com/downloads/) VS 2017 またはそれ以降、WinML アプリケーションを作成する開発者向け拡張機能。

Windows 10、バージョンが 1903 以降で**mlgen**は不要になった、Windows 10 SDK に含まれるので、ダウンロードして、拡張機能をインストールする必要があります。 1 つ[Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)とに 1 つずつ[Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)します。

したら**mlgen** 、インストールされている、Visual Studio プロジェクト内、ONNX にファイルを追加、プロジェクトの**資産**フォルダー、および VS は新しいインターフェイス ファイルに Windows ML ラッパー クラスを生成します。 これらのクラスとメソッドを使用すると、モデルをアプリケーションに統合します。 参照してください[チュートリアル。Windows Machine Learning の UWP アプリケーションの作成 (C#)](get-started-uwp.md)チュートリアルでは、このメソッドを使用して、モデルを統合します。

[!INCLUDE [help](../includes/get-help.md)]
