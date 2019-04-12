---
author: rosanevallim
title: Mlgen を使用した自動コード生成
description: Windows の ML のコード ジェネレーター mlgen インターフェイスを作成します (C#、 C++/WinRT、およびC++/CX) 簡単に読み込み、バインド、およびアプリでのモデルを評価することができます。
ms.author: rovalli
ms.date: 2/12/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: 35097655e99cf0eb7843eca266f648c0aa68161d
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474129"
---
# <a name="automatic-code-generation-with-mlgen"></a>Mlgen を使用した自動コード生成

<br/>

> [!VIDEO https://www.youtube.com/embed/8MCDSlm326U]

<br/>

Windows Machine Learning のコード ジェネレーター **mlgen**インターフェイスを作成します (C#、 [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)、およびC++/CX) ラッパー クラスを呼び出し、 [Windows ML API](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)のバインド、およびプロジェクトでモデルを評価する、簡単に読み込むには、することができます。

**mlgen**として提供されて、 [Visual Studio](https://visualstudio.microsoft.com/downloads/) VS 2017 またはそれ以降、WinML アプリケーションを作成する開発者向け拡張機能。

Windows 10、バージョンが 1903 以降で**mlgen**は不要になった、Windows 10 SDK に含まれるので、ダウンロードして、拡張機能をインストールする必要があります。 1 つ[Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=WinML.mlgen)とに 1 つずつ[Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WinML.mlgenv2)します。

したら**mlgen** 、インストールされている、Visual Studio プロジェクト内、ONNX にファイルを追加、プロジェクトの**資産**フォルダー、および VS は新しいインターフェイス ファイルに Windows ML ラッパー クラスを生成します。 これらのクラスとメソッドを使用すると、モデルをアプリケーションに統合します。 参照してください[チュートリアル。Windows Machine Learning の UWP アプリケーションの作成 (C#)](get-started-uwp.md)チュートリアルでは、このメソッドを使用して、モデルを統合します。

[!INCLUDE [help](includes/get-help.md)]
