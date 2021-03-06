---
author: walrusmcd
title: モデルをアプリに統合する
description: Windows ML を使用して Windows アプリケーションにトレーニング済みの機械学習モデルを統合する方法について説明します。
ms.author: paulm
ms.date: 5/19/2020
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 956e6bdb39d82712b7ed7c6a761639a4ab8578bc
ms.sourcegitcommit: f41fad7e6b6280bbbaf4157703f03fb7f23de676
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631826"
---
# <a name="integrate-a-model-into-your-app-with-windows-ml"></a>Windows ML でモデルをアプリに統合する

このガイドでは、Windows ML API を使用してモデルを Windows アプリに統合する方法について説明します。 別の方法として、Windows ML の自動コード ジェネレーターを使用する場合は、[mlgen](mlgen.md) を確認してください。

> **重要な API**:[Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)

次に挙げる Windows ML の基本的な構成要素について説明します。

* モデル
* セッション
* デバイス
* バインド

これらを使用して、Windows ML でモデルの読み込み、バインド、評価を行います。

また、[GitHub のサンプル アプリ](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)を参照して、エンド ツー エンドの Windows ML コード例を確認することもお勧めします。

次の動画では、これらの API の動作を短いデモで紹介します。

<br/>

> [!VIDEO https://www.youtube.com/embed/Nc2wstifyoE]

## <a name="using-winml-apis-in-c"></a>C++ での WinML API の使用

WinML API は C++/Cx と C++/WinRT の両方で使用できますが、C++/WinRT バージョンを使用することをお勧めします。C++ のコーディングがより自然にでき、開発作業のほとんどを、開発を先に進めるために注力できるためです。 C++/WinRT API を使用する個々の状況に応じて、以下の手順に従ってください。

* Windows 1803 以前を対象にする場合、「[チュートリアル:既存の WinML アプリを NuGet パッケージに移植する](port-app-to-nuget.md)」を参照します。
* 新しい C++ アプリケーションを作成する場合は、「[チュートリアル:Windows Machine Learning デスクトップ アプリケーションの作成 (C++) ](https://docs.microsoft.com/windows/ai/get-started-desktop)」を参照し、「**モデルを読み込む**」までのステップを実行します。
* (C++/WinRT 用にまだ設定されていない) 既存の C++ アプリケーションがある場合は、次の手順に従って、C++/WinRT 用にアプリケーションを設定します。
    1. 最新バージョンの [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (任意のエディション) がインストールされていることを確認します。
    2. [Windows 10 向け SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) バージョン 1803 以降が用意されていることを確認します。
    3. [Visual Studio Marketplace](https://marketplace.visualstudio.com/) から [C++/WinRT Visual Studio 拡張機能 (VSIX)](https://aka.ms/cppwinrt/vsix) をダウンロードしてインストールします。
    4. プロジェクトの .vcxproj ファイルに `<CppWinRTEnabled>true</CppWinRTEnabled>` プロパティを追加します。
        ```xml
        <Project ...>
            <PropertyGroup Label="Globals">
                <CppWinRTEnabled>true</CppWinRTEnabled>
        ...
        ```
    5. C++/WinRT には C++17 標準の機能が必要なため、プロジェクト プロパティの **[C/C++] > [言語] > [C++ 言語標準] > [ISO C++17 標準 (/std:c++17)]** を設定します。
    6. **[準拠モード:はい (/permissive-)]** をプロジェクト プロパティで設定します。
    7. 注意すべきもう 1 つのプロジェクト プロパティは、 **[C/C++] > [全般] > [警告をエラーとして扱う]** です。 これを好みに合わせて **[はい (/WX)]** または **[いいえ (/WX-)]** に設定します。 場合によっては、**cppwinrt.exe** ツールによって生成されたソース ファイルは、それらに実装を追加するまで警告を生成します。
    8. また、VSIX は、C++/WinRT の投影された型の Visual Studio ネイティブのデバッグの視覚化 (NatVis) を提供し、C# デバッグと同様のエクスペリエンスを実現します。 Natvis はデバッグ ビルドで自動で行われます。 シンボル **WINRT_NATVIS** を定義することで、リリース ビルドを選択できます。
    9. これで、プロジェクトが C++/WinRT 用に設定されました。 詳細については、「[C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)」を参照してください。

## <a name="related-topics"></a>関連トピック

* [mlgen](mlgen.md)
* [パフォーマンスとメモリ](performance-memory.md)
* [API リファレンス](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [コード例](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)

[!INCLUDE [help](../includes/get-help.md)]
