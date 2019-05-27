---
author: eliotcowley
title: Vision スキルのデスクトップ アプリケーションの作成 (C++)
description: Windows のビジョンのスキルを使用する Windows デスクトップ アプリケーション (非 UWP) を作成する方法について説明します。
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: windows 10、windows の ai windows ビジョンのスキルをデスクトップ
ms.localizationpriority: medium
ms.openlocfilehash: d61417a200902979ed8cfa5d9f37ab5b1b078e15
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179884"
---
# <a name="tutorial-create-a-vision-skill-desktop-application-c"></a>チュートリアル:Vision スキルのデスクトップ アプリケーションの作成 (C++)

> [!NOTE]
> いくつかの情報は、リリース版の発売までに著しく変更される可能性がありますが、リリース前の製品に関連します。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

> [!NOTE]
> 場合は、Win32 や .NET Core のデスクトップ アプリケーションなどの非 UWP アプリで使用する必要があるスキルを作成します。
スキルは、環境の対応しているかどうかを確認するスキルを変更する必要があります。

このチュートリアルで学習する方法。

- コンテナー対応スキル パッケージを変更します。
- マニフェストとヘッダー ファイルを提供します。

---

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (または Visual Studio 2017 バージョン 15.7.4 またはそれ以降)
- Windows 10、1809 またはそれ以降のバージョン
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)、1809 またはそれ以降のバージョン

---

1. スキルが UWP コンテナー対応であることを確認します。

- スキルからコンテナー環境のアプリを検出します。

コード例:

```cpp
// helper function to determine if the skill is being called from a UWP app container or not.
bool IsUWPContainer()
{
    HANDLE hProcessToken = INVALID_HANDLE_VALUE;
    HANDLE hProcess;
    hProcess = GetCurrentProcess();

    if (!OpenProcessToken(hProcess, TOKEN_QUERY, &hProcessToken))
    {
        throw winrt::hresult(HRESULT_FROM_WIN32(GetLastError()));
    }

    BOOL bIsAppContainer = false;
    DWORD dwLength;

    if (!GetTokenInformation(hProcessToken, TokenIsAppContainer, &bIsAppContainer, sizeof(bIsAppContainer), &dwLength))
    {
        // if we were denied token information we are definitely not in an app container.
        bIsAppContainer = false;
    }

    return bIsAppContainer;
}
```

- スキルが、UWP アプリ コンテナーまたは UWP のパッケージ化されたコンテナーから呼び出された場合、ファイル アクセスは、アプリ パッケージのパスに制限されます。 そのため、任意のモデル ファイルまたは依存関係は、パッケージ化、およびコンテナーのパスから読み込まれた必要。
ただし、スキルが通常の win32 cpp または .net core のデスクトップ アプリなどの非コンテナー環境から呼び出される場合、アプリ コンテナーの環境は使用できません。 代わりに、ディスクへのアクセスのほとんどは、スキルを使用するデスクトップ アプリのアクセス許可に従って使用可能になります。 スキルの dll の場所に同じ場所にあるモデル ファイルとその他のリソースを保持することをお勧め可能性があります。

コード例:

```csharp
winrt::Windows::Storage::StorageFile modelFile = nullptr;
if (IsUWPContainer())
{
    auto modelFile = Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri(L"ms-appx:///Contoso.FaceSentimentAnalyzer/" + WINML_MODEL_FILENAME)).get();
}
else
{
    WCHAR DllPath[MAX_PATH] = { 0 };
    GetModuleFileName(NULL, DllPath, _countof(DllPath));
    auto file = Windows::Storage::StorageFile::GetFileFromPathAsync(DllPath).get();
    auto folder = file.GetParentAsync().get();
    modelFile = folder.GetFileAsync(WINML_MODEL_FILENAME).get();
```

1. アプリ開発者のコア (nuget パッケージ) のヘッダー ファイル (.h) との Win32 cpp や .net で利用しやすくするための .manifest ファイルを提供します。

a.  ヘッダー ファイルC++アプリ

- WINRT cpp コンポーネント = > プロジェクトのプロパティには、MIDL が]-> [出力]-> [ヘッダー ファイル]-> [
- WinRTC#コンポーネント = > winmdidl ツールに .winmd を .idl; に変換するにはmidlrt .idl をヘッダー ファイルに変換します。
- .Idl を生成します。 winmd winmdidl <filename.winmd> /utf8 /metadata_dir:<path-to-sdk-unionmetadata> /metadata_dir: <path-to-additional-winmds> /outdir:<output-path>
- .Idl midlrt < filename.idl >/metadata_dir < パスにする-sdk-unionmetadata >/ns_prefix から .h を常に生成します。

    b.  マニフェストにパッケージ化されたアプリでスキルのサイド バイ サイドの読み込み: しました。 形式:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v3" manifestVersion="1.0">
    <assemblyIdentity
        type="win32"
        name="manifest Identityname preferable same as dll name without extension and same as filename of this manifest"
        version="1.0.0.0"/>

<file name="name of dll of the skill component including extension">

<activatableClass
    name="runtimeclassname1"
    threadingModel="both"
    xmlns="urn:schemas-microsoft-com:winrt.v1" />
<activatableClass
    name="runtimeclassname2"
    threadingModel="both"
    xmlns="urn:schemas-microsoft-com:winrt.v1" />

</file>
</assembly>
```

アプリ側のマニフェスト形式:
<div style="text-align:center" markdown="1">

![WinRT コンポーネントの読み込みの SxS のマニフェストのダイアグラム](../images/vision-skills-manifest.png)

</div>

```xml

<?xml version="1.0" encoding="utf-8"?>
<assembly manifestVersion="1.0" xmlns="urn:schemas-microsoft-com:asm.v1">
    <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>
    <dependency>
        <dependentAssembly>
            <assemblyIdentity
                type="win32"
                name="Microsoft.AI.Skills.SkillInterfacePreview"
                version="1.0.0.0"/>
        </dependentAssembly>
    </dependency>

    <dependency>
        <dependentAssembly>
            <assemblyIdentity
                type="win32"
                name="<name-of-manifest-file-without-extension>"
                version="1.0.0.0"/>
        </dependentAssembly>
    </dependency>

</assembly>
```

## <a name="next-steps"></a>次のステップ

誕生日おめでとう、スキルする準備ができましたデスクトップ アプリケーションで使用します。 サンプルの完全なソース コードは GitHub で入手できますがまもなくされます。
の他のサンプルでいろいろ[GitHub](https://github.com/Microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill)し、自由に拡張します。

[!INCLUDE [help](../includes/get-help-vision.md)]
