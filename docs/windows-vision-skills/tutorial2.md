---
title: デスクトップアプリから Windows 構想スキルを利用する (C++)
description: デスクトップアプリケーション (UWP 以外) で Windows ビジョンのスキルを準備して使用する方法について説明します。
ms.author: lobourre
ms.date: 8/26/2019
ms.topic: article
keywords: windows 10、windows ai、windows ビジョンスキル、デスクトップ
ms.localizationpriority: medium
ms.openlocfilehash: 0a5b8e1068bceaa805667d5d4c88495d80c290b7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156168"
---
# <a name="tutorial-create-a-vision-skill-desktop-application-c"></a>チュートリアル:ビジョンスキルデスクトップアプリケーション (C++) を作成する

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 Microsoft は、ここで提供される情報に関して、明示または黙示を問わず、いかなる保証も行いません。

> [!NOTE]
> UWP 以外のアプリ (Win32 または .NET Core デスクトップアプリケーションなど) で使用する必要がある Windows 構想スキルを作成する場合は、その実行時環境についてスキルが認識していることを確認する必要があります。

このチュートリアルでは、次の方法について説明します。

- 実行時環境を認識するようにスキルパッケージを変更します。 具体的には、このスキルは、UWP アプリコンテナー内で実行されているかどうかを認識している必要があります。
- 技術が UWP 以外のアプリで機能するために必要なマニフェストファイルとヘッダーファイルを提供します。

---

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)(または Visual Studio 2017、バージョン15.7.4 以降)
- Windows 10 バージョン 1809 以降
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)バージョン1809以降

---

1. 実行時に、スキルが UWP に対応していることを確認します。

- 技術の内部から UWP アプリコンテナーのランタイム環境を検出します。

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

- 技術が UWP アプリコンテナーまたは UWP パッケージコンテナーから呼び出された場合、ファイルアクセスはアプリケーションパッケージパスに制限されます。 そのため、モデルファイルまたは依存関係は、パッケージ化し、コンテナーパスから読み込む必要があります。

ただし、スキルが Win32 C++や .Net Core 3.0 デスクトップアプリなどの非コンテナー環境から呼び出された場合、UWP アプリコンテナー環境は使用できません。 代わりに、ほとんどのディスクアクセスは、スキルを消費するデスクトップアプリのアクセス許可に従って利用できるようになります。 そのため、モデルファイルとその他のリソースは、スキルのライブラリ ( *.dll*) の場所と同じ場所に保持することをお勧めします。

コード例:

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

2. (Nuget でパッケージ) ヘッダーファイル (.h) と*マニフェスト*ファイルを提供して、Win32 または .Net Core 3.0 アプリ開発者が使いやすいようにします。

    2.1. アプリのヘッダーファイル ( *.h*) をC++生成します。
Visual Studio で、プロジェクトを選択します。 次のコードも同様の結果になります。
    - WinRT C++コンポーネント:[プロジェクト-> のプロパティ-> MIDL-> 出力-> ヘッダーファイル] を選択します。
    - WinRT C#コンポーネント:プロジェクトC#にヘッダーファイルを生成するオプションがないため、最初に生成されたメタデータファイル (*winmd*) をインターフェイス定義ファイル ( *.idl*) に変換してから、これらの *.idl*をヘッダーファイル ( *.h*) に変換する必要があります。 これは、Visual Studio 開発者コマンドプロンプトを使用して実行できます。
      - [Winmdidl](https://docs.microsoft.com/cpp/cppcx/wrl/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata?view=vs-2019)を使用して、 *winmd*から .idl を生成*し*ます。
      ```
      > winmdidl <filename.winmd> /utf8 /metadata_dir:<path-to-sdk-unionmetadata> /metadata_dir: <path-to-additional-winmds> /outdir:<output-path>
      ```
      - [Midlrt](https://docs.microsoft.com/windows/win32/midl/midlrt-and-windows-runtime-components)を使用して *.idl*から *.h*を生成する
      ```
      > midlrt <filename.idl> /metadata_dir  <path-to-sdk-unionmetadata> /ns_prefix
      ```

    2.2. マニフェストファイルを作成して、パッケージ化されていないアプリのスキルをサイドバイサイドで登録できるようにします。 このファイルには、WinRT コンポーネントで定義されているランタイムクラスが一覧表示されるため、実行時に登録して読み込むことができます。 インターフェイス定義ファイル (*idl*) を解析することによってマニフェストを作成できる[便利なスクリプト](https://github.com/microsoft/WindowsVisionSkillsPreview/blob/master/samples/Scripts/genSxSManifest.ps1)が用意されています。 エンドツーエンドのデモンストレーションについては、[スキルのサンプル](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples/SentimentAnalyzerCustomSkill)を参照してください。


    2.2.1. Side-by-side マニフェストの形式:

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

2.3. アプリで、生成したスキルマニフェストを示すマニフェストファイルを追加します。

3.1. アプリケーション側のマニフェストファイルとサイドマニフェストファイルの形式を生成するアプリプロジェクトの設定:
<div style="text-align:center" markdown="1">

![WinRT コンポーネントの SxS 読み込みのマニフェストの図](../images/vision-skills-manifest.png)

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

バンザイ、スキルをデスクトップアプリケーションで使用する準備ができました。 [GitHub](https://github.com/microsoft/WindowsVisionSkillsPreview/tree/master/samples)でスキルのサンプルを使ってみてください。

[!INCLUDE [help](../includes/get-help-vision.md)]
