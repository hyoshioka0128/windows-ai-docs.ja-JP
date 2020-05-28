---
author: QuinnRadich
title: 既存の WinML アプリを NuGet パッケージに移植する
description: 既存の WinML デスクトップ アプリケーションを移植して、再頒布可能 NuGet パッケージを使用する方法について説明します。
ms.author: quradic
ms.date: 5/19/2020
ms.topic: article
keywords: Windows 10、Windows AI、Windows ML、WinML、Windows Machine Learning、NuGet
ms.localizationpriority: medium
ms.openlocfilehash: 56ab40ca13c5ca46d21ca4b6ea7bc207920ad440
ms.sourcegitcommit: f41fad7e6b6280bbbaf4157703f03fb7f23de676
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83632804"
---
# <a name="port-an-existing-winml-app-to-nuget-package-c"></a>既存の WinML アプリを NuGet パッケージ (C++) に移植する 

このチュートリアルでは、既存の WinML デスクトップ アプリケーションを移植して、[再頒布可能 NuGet パッケージ](https://github.com/microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection/Desktop/cpp)を使用する方法について説明します。 

## <a name="prerequisites"></a>前提条件

* WinML アプリケーション。 新しいアプリケーションを作成する場合は、次をご覧ください。チュートリアル:Windows Machine Learning デスクトップ アプリケーション (C++) の作成 
* Windows 8.1 以上 
* Visual Studio 2019 (または Visual Studio 2017 バージョン 15.7.4 以降)

## <a name="add-the-nuget-package-to-your-project"></a>NuGet パッケージをプロジェクトに追加する

既存のアプリケーションの Visual Studio プロジェクトで、ソリューション エクスプローラーに移動し、 **[ソリューションの NuGet パッケージの管理]** を選択します。 `Microsoft.AI.MachineLearning` NuGet パッケージを選択します。 適切なプロジェクトに追加していることを確認し、 **[インストール]** を押します。

次に、ソリューションをもう一度ビルドします。 C++/WinRT ツールキットは `Microsoft.AI.MachineLearning` NuGet パッケージから新しいヘッダーとメタデータを解析することにより、次の手順で混乱が生じないようにします。

## <a name="include-the-new-header"></a>新しいヘッダーを含める

ベスト プラクティスとして、コントロール フラグを追加し、アプリでインボックス Windows ML と NuGet パッケージを相互に切り替えることができるようにする必要があります。

```c++
#ifdef USE_WINML_NUGET
#include “winrt/Microsoft.AI.MachineLearning.h” 
#endif
```

## <a name="change-the-namespace"></a>名前空間を変更する

次に、コントロール フラグを使用して、`Windows::AI::Machinelearning` を `Microsoft::AI::MachineLearning` 名前空間に切り替えることができるようにします。 この変更を行うと、該当する場合は、コードで NuGet パッケージが自動的に使用されます。

```c++
#ifdef USE_WINML_NUGET 

Using namespace Microsoft::AI::MachineLearning 

#else 

Using namespace Windows::AI::MachineLearning 

#endif 
```

## <a name="change-the-preprocessor-definitions"></a>プリプロセッサ定義を変更する

ここで、 **[ソリューション エクスプローラー]** でプロジェクトを右クリックし、 **[プロパティ]** を選びます。 **[プロパティ]** ウィンドウで、 **[プリプロセッサ]** ページを選びます。 **[プリプロセッサの定義]** を編集し、それを `USE_WINML_NUGET:_DEBUG` に変更します。

## <a name="build-and-run"></a>ビルドして実行

アプリケーションで WinML NuGet パッケージが正常に使用されるようになりました。