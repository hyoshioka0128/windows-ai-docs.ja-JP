---
author: walrusmcd
title: モデルをアプリに統合します。
description: Windows の ML を使用して、トレーニング済みのマシン学習モデルを Windows アプリケーションに統合する方法について説明します。
ms.author: paulm
ms.date: 2/15/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: e9a09d798afe163be399b50d31bc4a8a2e85b96a
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475019"
---
# <a name="integrate-a-model-into-your-app-with-windows-ml"></a>Windows ML でモデルをアプリに統合する

このガイドでは、Windows の ML Api を使用してモデルを Windows アプリに統合する方法を取り上げます。 または、Windows の ML の自動コード ジェネレーターを使用する場合は、チェック アウト[mlgen](mlgen.md)します。

> **重要な API**:[Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)

Windows の ML の構成の基本的な要素を移動します。

* モデル
* セッション
* デバイス
* バインド

読み込み、バインド、および Windows ML を使用したモデルを評価するには、これらを使用します。

見てお勧め、[サンプル github アプリ](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)をエンド ツー エンド Windows ML コード例を参照してください。

次のビデオでは、短いデモでは、実行中これらの Api を示します。

<br/>

> [!VIDEO https://www.youtube.com/embed/Nc2wstifyoE]

## <a name="using-winml-apis-in-c"></a>WinML Api を使用します。C++

WinML Api は両方で使用できるC++/CX とC++/WinRT、使用をお勧め、C++ほどの/WinRT バージョンより自然C++コーディングして、ほとんどの開発作業を集中するは今後します。 使用する特定の状況に関連する以下の手順を利用できる、 C++WinRT Api:

* 新しいを作成する場合C++アプリケーションを参照してください[チュートリアル。Windows Machine Learning のデスクトップ アプリケーションの作成 (C++)](https://docs.microsoft.com/windows/ai/get-started-desktop)までの手順と**モデルを読み込み、** します。
* 既にある場合C++アプリケーション (これが既に設定されていないサインアップC++/WinRT)、用のアプリケーションを設定する次の手順に従ってC++/WinRT:
    1. 最新バージョンがあるかどうかを確認[Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) (任意のエディション) をインストールします。
    2. 必ず、 [SDK for Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk)、バージョン 1803 以降。
    3. ダウンロードしてインストール、 [ C++WinRT Visual Studio Extension (VSIX)](https://aka.ms/cppwinrt/vsix)から、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)します。
    4. 追加、`<CppWinRTEnabled>true</CppWinRTEnabled>`プロパティをプロジェクトの .vcxproj ファイル。
        ```xml
        <Project ...>
            <PropertyGroup Label="Globals">
                <CppWinRTEnabled>true</CppWinRTEnabled>
        ...
        ```
    5. C++/WinRT には、機能が必要です。 から c++ 17 標準、そのため、プロジェクトのプロパティ設定**C/C++ > 言語 >C++言語標準 > ISO c++ 17 標準 (//std:c + + 17)** します。
    6. 設定**準拠モード。[はい] (/permissive -)** プロジェクトのプロパティ。
    7. 注意すべきもう 1 つのプロジェクト プロパティは**C/C++ > [全般] > 警告をエラーとして扱う**します。 これを設定**はい (/WX)** または**いいえ (/WX-)** を体験します。 場合によっては、ソースによって生成されたファイル、 **cppwinrt.exe**ツールは、それらへの実装を追加するまでに警告を生成します。
    8. VSIX もわかります (natvis) Visual Studio のネイティブのデバッグの視覚化のC++/WinRT のようなエクスペリエンスを提供する型を射影するC#デバッグします。 Natvis はデバッグ ビルドで自動で行われます。 シンボルを定義することで、リリース ビルドを選択できます**WINRT_NATVIS**します。
    9. プロジェクトには、セットアップがなりますC++/WinRT です。 参照してください[ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)詳細についてはします。

## <a name="related-topics"></a>関連トピック

* [mlgen](mlgen.md)
* [パフォーマンスとメモリ](performance-memory.md)
* [API リファレンス](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)
* [コード例](https://github.com/Microsoft/Windows-Machine-Learning/tree/master)

[!INCLUDE [help](includes/get-help.md)]
