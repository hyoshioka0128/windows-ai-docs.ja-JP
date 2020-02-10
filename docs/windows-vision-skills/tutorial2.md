---
title: デスクトップ アプリから Windows Vision Skills を使用する (C++)
description: デスクトップ アプリケーション (UWP 以外) で Windows Vision Skills を準備して使用する方法について説明します。
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: windows 10, windows ai, windows vision skills, デスクトップ
ms.localizationpriority: medium
ms.openlocfilehash: 0a5b8e1068bceaa805667d5d4c88495d80c290b7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156168"
---
# <a name="tutorial-create-a-vision-skill-desktop-application-c"></a>チュートリアル: ビジョン スキルのデスクトップ アプリケーションを作成する (C++)

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

> [!NOTE]
> UWP 以外のアプリ (Win32 または .NET Core デスクトップ アプリケーションなど) で使用する必要がある Windows Vision Skills を作成する場合は、スキルにそのランタイム環境を確実に認識させる必要があります。

このチュートリアルでは、次の方法について説明します。

- ランタイム環境が認識されるようにスキル パッケージを変更する。 具体的には、UWP アプリ コンテナー内で実行されているかどうかをスキルに認識させる必要があります。
- スキルが UWP 以外のアプリで機能するために必要なマニフェスト ファイルとヘッダー ファイルを提供する。

---

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (または Visual Studio 2017 バージョン 15.7.4 以降)
- Windows 10 バージョン 1809 以降
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) バージョン 1809 以降

---

1. スキルが実行時に UWP コンテナーを認識することを確認します。

- スキルの内部から UWP アプリ コンテナーのランタイム環境を検出します。

コードの例:

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

- スキルが UWP アプリ コンテナーまたは UWP パッケージ コンテナーから呼び出された場合、ファイル アクセスはアプリケーション パッケージ パスに制限されます。 そのため、すべてのモデル ファイルまたは依存関係は、パッケージ化してコンテナー パスから読み込まれるようにする必要があります。

ただし、スキルが Win32 C++ や .Net Core 3.0 デスクトップ アプリなどの非コンテナー環境から呼び出された場合、UWP アプリ コンテナー環境は使用できません。 代わりに、ほとんどのディスク アクセスは、スキルを使用するデスクトップ アプリのアクセス許可に従って利用できるようになります。 そのため、モデル ファイルとその他のリソースは、スキルのライブラリ ( *.dll*) と同じ場所に保持することをお勧めします。

コードの例:

```csharp
winrt::Windows::Storage::StorageFile modelFile = nullptr;

// if running from within a UWP app container, access resources using a URI relative to its path
if (IsUWPContainer())
{
    auto modelFile = Windows::Storage::StorageFile::GetFileFromApplicationUriAsync(Windows::Foundation::Uri(L"ms-appx:///Contoso.FaceSentimentAnalyzer/" + WINML_MODEL_FILENAME)).get();
}
// If running from a regular app process such as a Desktop app, access resources using the full system path
else
{
    WCHAR DllPath[MAX_PATH] = { 0 };
    GetModuleFileName(NULL, DllPath, _countof(DllPath));
    // Get path of current DLL
    auto file = Windows::Storage::StorageFile::GetFileFromPathAsync(DllPath).get();
    // Use the path of the parent directory to access other resources bundled with the DLL
    auto folder = file.GetParentAsync().get();
    modelFile = folder.GetFileAsync(WINML_MODEL_FILENAME).get();
```

2. Win32 または .Net Core 3.0 アプリ開発者が使いやすいように、ヘッダー ファイル (.h) と *.manifest* ファイルを提供します (NuGet のパッケージ)。

    2.1. C++ アプリのヘッダー ファイル ( *.h*) を生成します。
Visual Studio で、プロジェクトを選択します。 次のようになります。
    - WinRT C++ コンポーネント:[Project]/(プロジェクト/) -> [properties]/(プロパティ/) -> [MIDL] -> [output]/(出力/) -> [Header File]/(ヘッダー ファイル/) を選択します
    - WinRT C# コンポーネント:C# プロジェクトにヘッダー ファイルを生成するオプションがないため、最初に、生成されたメタデータ ファイル ( *.winmd*) をインターフェイス定義ファイル ( *.idl*) に変換してから、その *.idl* をヘッダー ファイル ( *.h*) に変換する必要があります。 この操作は Visual Studio の開発者コマンド プロンプトを使用して実行できます。
      - [winmdidl.exe](https://docs.microsoft.com/cpp/cppcx/wrl/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata?view=vs-2019) を使用して *.winmd* から *.idl* を生成します
      ```
      > winmdidl <filename.winmd> /utf8 /metadata_dir:<path-to-sdk-unionmetadata> /metadata_dir: <path-to-additional-winmds> /outdir:<output-path>
      ```
      - [midlrt.exe](https://docs.microsoft.com/windows/win32/midl/midlrt-and-windows-runtime-components) を使用して *.idl* から *.h* を生成します
      ```
      > midlrt <filename.idl> /metadata_dir  <path-to-sdk-unionmetadata> /ns_prefix
      ```

    2.2. パッケージ化されていないアプリでのスキルの side-by-side 登録を可能にするマニフェスト ファイルを作成します。 このファイルには、WinRT コンポーネントで定義されているランタイム クラスがリストされているため、実行時に登録して読み込むことができます。 インターフェイス定義ファイル (*idl*) を解析してマニフェストを作成できる[便利なスクリプト](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/Scripts/genSxSManifest.ps1)が提供されています。 エンドツーエンドのデモンストレーションについては、[スキルのサンプル](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill) を参照してください。


    2.2.1. side-by-side マニフェストの形式:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <assembly xmlns="urn:schemas-microsoft-com:asm.v3" manifestVersion="1.0">
        <assemblyIdentity
        type="win32"
        name="manifest Identityname, preferably same as dll name without extension and same as filename of this manifest"
        version="1.0.0.0"/>

        <file name="dll name of the skill component, including extension">

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

2.3. ご使用のアプリに、上記で生成したスキル マニフェストを示すマニフェスト ファイルを追加します。

2.3.1. アプリ サイド マニフェスト ファイルを生成するためのアプリ プロジェクト設定とサイド マニフェスト ファイルの形式:
<div style="text-align:center" markdown="1">

![WinRT コンポーネントの SxS 読み込みのためのマニフェストの図](../images/vision-skills-manifest.png)

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

## <a name="next-steps"></a>次の手順

スキルをデスクトップ アプリケーションで使用する準備ができました。 [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples) のスキルのサンプルを使用して、お好きなように拡張してみてください。

[!INCLUDE [help](../includes/get-help-vision.md)]
