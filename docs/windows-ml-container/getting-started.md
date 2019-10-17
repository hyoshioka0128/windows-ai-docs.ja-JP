---
title: Windows ML コンテナーを使ってみる
description: IoT デバイスで Windows ML コンテナーの使用を開始する
ms.date: 10/14/2019
ms.topic: article
keywords: windows 10、windows ml コンテナー、ml、ai、コンテナー、iot、エッジ
ms.localizationpriority: medium
ms.openlocfilehash: 729d348a5606b97fd493382609919dac730edc76
ms.sourcegitcommit: e08b8ae92e48c1b82bb6f94fefcb32cd817453d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443022"
---
# <a name="getting-started"></a>開始するには

Windows ML コンテナーは、IoT および Windows ML 開発の基礎を理解している開発者が使用することを意図しています。 Windows ML の使用方法の詳細については、 [WINDOWS ml のドキュメント](../windows-ml/index.md)を参照してください。

## <a name="prerequisites-and-environment-setup"></a>前提条件と環境のセットアップ

Windows の Insider バージョンをインストールするには、 [Windows Insider プログラムに参加](https://insider.windows.com/register/)する必要があります。

Windows ホストの Insider リリースをインストールしたら、コマンドプロンプトで `winver` を実行してホストのバージョンを見つけることができます。

![winver](./images/winver.png)

上記の例では、ホストバージョンは `18999.1` です。

### <a name="host-os-and-container-version-matching-requirements"></a>ホスト OS とコンテナーバージョンの一致要件

Windows ML コンテナーは、Windows Enterprise ホスト上で実行されます。 Windows ML コンテナーのバージョンは、**高速リング windows 10 Insider Preview ビルド (20H1)** のバージョンと完全に一致している必要があります。

### <a name="windows-ml-container-on-docker-hub"></a>Docker hub の Windows ML コンテナー

ホストのバージョンを特定したら、[ [WINDOWS ML コンテナー Insider]](https://hub.docker.com/_/microsoft-windows-ml-insider)の [Docker Hub] ページで一致するタグを見つけます。 対応するバージョンタグと Docker プル URL を見つけます。

```console
10.0.18999.1 (20H1)
docker pull mcr.microsoft.com/windows/ml/insider:10.0.18999.1
```

### <a name="visual-studio-2019"></a>Visual Studio 2019

Windows ML コンテナー用に開発する場合は、Visual Studio 2019 を使用することをお勧めします。 最新の Community edition は、 [Visual Studio サイトから](https://visualstudio.microsoft.com/vs/)無料で入手できます。 以前に Visual Studio を使用していない場合は、詳細についてサイトの指示とガイダンスに従ってください。

Visual Studio のインストールを構成するときに、次のパッケージがインストールされていることを確認してください。
- ユニバーサル Windows プラットフォームの開発
- .NET Core クロスプラットフォーム development.NET コア2.2 開発ツール

![vs_install1](./images/vs_install1.png)

![vs_install2](./images/vs_install2.png)

### <a name="windows-sdk-insider-preview"></a>Windows SDK Insider Preview

Windows ML コンテナーと Windows SDK Insider Preview のバージョンができるだけ近いものであることを確認します。 正確なバージョンの一致は必要ありませんが、不一致が大きいほど、エラーやその他の問題が発生する可能性が高くなります。

[最新の Insider SDK については、こちらを参照してください。](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)

### <a name="configure-visual-studio-2019-nuget-package-source"></a>Visual Studio 2019 NuGet パッケージソースの構成

Windows ML コンテナーがプレビュー段階にある間、 [Windows ヘッドレス WinRT コントラクト](api-list.md)は、別のパッケージソースから NuGet パッケージを通じて提供されます。

次のソースがパッケージソースにあることを確認します。

- https://api.nuget.org/v3/index.json
- https://pkgs.dev.azure.com/WindowsSDK/PublicArtifactsPreview/_packaging/WindowsSDKFlight/nuget/v3/index.json

新しいソースを追加するには、次の手順を実行します。

- Visual Studio 2019 を開く
- [**ツール]-> NuGet パッケージマネージャー-> パッケージマネージャーの設定-** [パッケージソースの >] を選択し、パッケージ SDK のフライトソース URL を追加します。

![vs_install3](./images/vs_install3.png)

![vs_install4](./images/vs_install4.png)

### <a name="gpu-support"></a>GPU のサポート

コンテナーで GPU アクセラレータがサポートされるようにするには、次の要件を満たす GPU およびグラフィックスドライバーをホストで使用できる必要があります。

#### <a name="gpu-requirements"></a>GPU の要件


|Vendor (ベンダー)   |Architecture        |一般的な顧客向け GPU 名  |
|---------|--------------------|-----------------------------------|
|AMD      | GCN 4 以降     |Radeon RX 400 シリーズ以降、または Radeon Pro WX シリーズ|
|Intel    | Kaby Lake 以降 |Intel HD Graphics 600 シリーズ以降 |
|NVIDIA   | Kepler 以降    |GeForce 600 シリーズ以降、または Quadro K シリーズ以降|

#### <a name="graphics-driver-requirements"></a>グラフィックスドライバーの要件

|Vendor (ベンダー)|最小ドライバーバージョン  |
|------|--------------------|
|AMD   |26.20.12002.65 |
|Intel |26.20.100.6812 |
|NVIDIA|26.21.14.3086  |

GPU またはドライバーが上記の要件を満たしていない場合、またはコンテナーホスト OS が VM で実行されている場合は、CPU ベースの推論のみがサポートされます。

#### <a name="graphics-driver-installation"></a>グラフィックスドライバーのインストール

システムの最新のグラフィックスドライバーをダウンロードするには、設定 に移動し、 **& セキュリティ > の更新 Windows Update > 更新プログラムの確認 の**順に > します。

![driverupdate](./images/windowsupdate.png)

#### <a name="troubleshooting-graphics-driver"></a>グラフィックスドライバーのトラブルシューティング

ドライバーのバージョンが最小要件を満たしていることを確認します。そのためには、 **[デバイスマネージャー > ディスプレイアダプター]** に移動し、グラフィックスアダプターを右クリックして、 **[プロパティ]** を選択し、 **[ドライバー]** タブの下に表示します。

![解決](./images/troubleshoot.png)

最小バージョン要件を満たす Windows Update からグラフィックスドライバーをダウンロードできない場合は、システムの DxDiag 情報が添付されていることを電子メールで @no__t してください。 DxDiag 情報を実行して保存する手順については、[このサポートページを参照してください](https://support.microsoft.com/help/4028644/windows-open-and-run-dxdiagexe)。

## <a name="set-up-and-test-a-basic-environment"></a>基本環境のセットアップとテスト

1.  ホスト OS と Windows ML コンテナーイメージが同じバージョン番号を共有していることを確認します。

2.  ホスト OS で**コンテナー**機能を有効にします。

    *管理者特権*のコマンドウィンドウで、次のコマンドを実行します。  システムの再起動を求めるメッセージが表示される場合があります。

```console
dism /online /Enable-Feature /FeatureName:Containers
```

3.  Docker と dockerd .exe の夜間ビルドバージョンをダウンロードします。

```console
curl.exe -o %windir%\system32\dockerd.exe https://master.dockerproject.org/windows/x86_64/dockerd.exe
```
```console
curl.exe -o %windir%\system32\docker.exe https://master.dockerproject.org/windows/x86_64/docker.exe
```

Docker サービスを登録して開始します。

```console
dockerd.exe --register-service

net start docker
```

次の出力メッセージが表示されます。

```console
The Docker Engine service is starting.
The Docker Engine service was started successfully.
```

4.  次のコマンドを使用して、Docker が正しく実行されていることを確認できます。

```console
docker version
```

これにより、次の出力メッセージが生成されます。

```console
Client:
    Version:           master-dockerproject-2019-08-03
    API version:       1.40
    Go version:        go1.12.7
    Git commit:        e505a7c2
    Built:             Sun Aug  4 00:02:51 2019
    OS/Arch:           windows/amd64
    Experimental:      false

Server:
    Engine:
    Version:          master-dockerproject-2019-08-03
    API version:      1.41 (minimum version 1.24)
    Go version:       go1.12.7
    Git commit:       7449ca3
    Built:            Sun Aug  4 00:12:27 2019
    OS/Arch:          windows/amd64
    Experimental:     false
```

5.  Docker が起動したら、次のコマンドを使用して、コンテナーイメージファイルを Docker にインポートします。

```console
docker pull mcr.microsoft.com/windows/ml/insider:10.0.18999.1
docker tag mcr.microsoft.com/windows/ml/insider:10.0.18999.1 windowsml:latest
```

6.  イメージがインストールされたら、`docker images` を実行して、使用可能なすべてのコンテナーイメージを列挙できます。 既定では、このイメージにはリポジトリの名前またはタグがありません。 1つを指定することも、後の手順でイメージを参照するために提供されているハッシュからイメージ ID を使用することもできます。

出力は次のようになります。

```console
C:\Windows\system32>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              a9d5d08d079f        10 seconds ago      319MB

C:\Windows\system32>docker tag a9d5d08d079f windowsml:latest

C:\Windows\system32>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
windowsml           latest              a9d5d08d079f        25 seconds ago      319MB
```


7.  次のコマンドを使用して https://github.com/microsoft/Windows-Machine-Learning/releases/tag/1.2.1.1 から WinMLRunner v 1.2.1.1 をダウンロードします。

```console
curl -o WinMLRunner.zip -L https://github.com/microsoft/Windows-Machine-Learning/releases/download/1.2.1.1/WinMLRunner.v1.2.1.1.zip
```

次に、.zip を現在のフォルダーに解凍します。

8.  次のコマンドを使用して https://github.com/microsoft/Windows-Machine-Learning/tree/1.2.1.1/SharedContent/models から SqueezeNet onnx サンプルをダウンロードします。

```console
curl -o SqueezeNet.onnx -L https://github.com/microsoft/Windows-Machine-Learning/raw/1.2.1.1/SharedContent/models/SqueezeNet.onnx
```

9.  Dockerfile を作成して、インポートした Windows ML コンテナーイメージに必要なファイルをコピーします。

次のコマンドをコピーして、Dockerfile を直接作成できます。     

```console
echo FROM windowsml:latest               >  Dockerfile
echo WORKDIR C:/App                      >> Dockerfile
echo COPY ./x64/WinMLRunner.exe C:/App/  >> Dockerfile
echo COPY ./SqueezeNet.onnx C:/App/      >> Dockerfile
```

```console
C:\tgz>type Dockerfile
FROM windowsml:latest
WORKDIR C:/App
COPY ./x64/WinMLRunner.exe C:/App/
COPY ./SqueezeNet.onnx C:/App/
```


10. Dockerfile に基づいて、`docker build command` の新しいコンテナーを作成します。

```console
C:\tgz>docker build -t winmlrunner:latest .
```

結果は次のようになります。


```console
Sending build context to Docker daemon  5.525MB
Step 1/4 : FROM windowsml:latest
 ---> a9d5d08d079f
Step 2/4 : WORKDIR C:/App
 ---> Running in 37e9d759365f
Removing intermediate container 37e9d759365f
 ---> 8ab270ff4deb
Step 3/4 : COPY ./x64/WinMLRunner.exe C:/App/
 ---> 16e2b23a5de0
Step 4/4 : COPY ./SqueezeNet.onnx C:/App/
 ---> 05269bb7c5f8
Successfully built 05269bb7c5f8
Successfully tagged winmlrunner:latest

C:\tgz>docker images
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
winmlrunner         latest              ed74203b2655        About a minute ago   325MB
windowsml           latest              a9d5d08d079f        23 minutes ago       319MB
```

11. Windows ML コンテナーと WinMLRunner イメージに基づいて、GPU が有効なプロセス分離コンテナーを起動します。

```console
docker run -it --isolation process --device class/5B45201D-F2F2-4F3B-85BB-30FF1F953599 winmlrunner:latest cmd /k
```

Docker を使用して Windows ML コンテナーを実行するには、いくつかの重要な引数を指定する必要があります。

- `-it`  
    対話型シェルコンポーネントが `stdin` に転送し、`tty` を使用できるようにするために使用します。 この引数を省略した場合、コマンドラインインターフェイスは正常に機能しません。
- `--isolation process` は、コンテナーの種類をプロセス分離コンテナーとして指定します。
- `--device class/5B45201D-F2F2-4F3B-85BB-30FF1F953599` は、コンテナーに公開するデバイスのクラス GUID を指定します。 `class/5B45201D-F2F2-4F3B-85BB-30FF1F953599` は `GUID_DEVINTERFACE_DISPLAY_ADAPTER` を表します。これにより、DirectX Gpu が有効になります。
- `winmlrunner:latest` は、前の手順で作成された、実行するイメージを指定します。 これには、@no__t 0 のコマンドで指定したリポジトリの名前とタグ、またはイメージのイメージ ID/ハッシュを指定できます。 タグ名として**latest**を使用した場合は、省略できます。
- `cmd /k`  
    これは、docker がコンテナー内で実行するコマンドです。

12. コンテナーのコマンドラインから、CPU を使用して WinMLRunner を実行します。

```console
WinMLRunner.exe -model C:/App/SqueezeNet.onnx -cpu
```

次のような出力が表示されます。

```console
DXGI module not found.
Loading model (path = C:/App/SqueezeNet.onnx)...
=================================================================
Name: squeezenet_old
Author: onnx-caffe2
Version: 9223372036854775807
Domain:
Description:
Path: C:/App/SqueezeNet.onnx
Support FP16: false

Input Feature Info:
Name: data_0
Feature Kind: Float

Output Feature Info:
Name: softmaxout_1
Feature Kind: Float

=================================================================


Creating Session with CPU device
Binding (device = CPU, iteration = 1, inputBinding = CPU, inputDataType = Tensor, deviceCreationLocation = WinML)...[SUCCESS]
Evaluating (device = CPU, iteration = 1, inputBinding = CPU, inputDataType = Tensor, deviceCreationLocation = WinML)...[SUCCESS]
```
これで、Windows ML コンテナーを使用するように環境が正しくセットアップされました。

13. また、GPU を使用して WinMLRunner を実行することもできます。 @No__t-0 のコマンドライン引数を使用して、AMD Radeon、Nvidia、または Intel のいずれかを指定します。

```console
WinMLRunner.exe -model C:/App/SqueezeNet.onnx -GPUAdapterName [radeon/nvidia/intel]
```

## <a name="build-apps-the-for-windows-ml-container"></a>Windows ML コンテナー用のアプリをビルドする

### <a name="samples-for-windows-ml-container"></a>Windows ML コンテナーのサンプル

開始するには、前の手順に従って Visual Studio 2019 がセットアップおよび構成されていることを確認します。 その後、次のサンプルを試してみてください。

- [Customvision](https://github.com/imingc/Windows-Machine-Learning/tree/winml_container/Samples/CustomVision)。 このサンプルでは、 [Azure Custom Vision Service](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)によってトレーニングされたモデルを使用します。 トレーニング済みのモデルは[ONNX ファイルとしてエクスポート](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/custom-vision-onnx-windows-ml)され、コンテナー内で実行されるサンプルアプリの一部として含まれます。
- [SqueezeNetObjectDetection](https://github.com/microsoft/Windows-Machine-Learning/tree/master/Samples/SqueezeNetObjectDetection)。 このアプリ (cpp および c @ no__t-0 のみ) は、SqueezeNet モデルを使用してイメージ内の主要なオブジェクトを検出します。

### <a name="create-a-visual-studio-2019-c-project-from-scratch"></a>Visual Studio 2019 C#プロジェクトを最初から作成する

Windows ML コンテナーは、サイズが小さいため、 [Windows api のサブセット](api-list.md)のみをサポートしています。 Visual Studio プロジェクトを作成するときに、この小さな API サーフェイスを指定して、実行前にサポートされていない Api を検出できます。

ヘッドレス WinRT API コントラクトを使用するには、次のようにします。

1. Visual Studio 2019 で、新しい**C @ No__t Console App (.Net Core)** プロジェクトを作成します。

![vsproj](./images/vs_project1.png)

1. **ツール-> Nuget-> パッケージマネージャーコンソール** を選択します。

1. パッケージマネージャーコンソールで、次のように実行します。

```console
Install-Package Microsoft.Windows.SDK.Headless.Contracts -Prerelease
```

### <a name="create-a-visual-studio-2019-c-project-from-scratch"></a>Visual Studio 2019 C++プロジェクトを最初から作成する

1. Visual Studio 2019 で、新しい **C++コンソールアプリ**プロジェクトを作成します。

![vsproj](./images/vs_project2.png)

1. **ツール-> Nuget-> パッケージマネージャーコンソール** を選択します。

1. パッケージマネージャーコンソールで、次のように実行します。

```console
Install-Package Microsoft.Windows.SDK.Headless.Contracts -Prerelease
Install-Package Microsoft.Windows.CppWinRT -Version 2.0.190730.2
```

4. @No__t 使用するようにプロジェクトを更新する-0:
    1. プロジェクトを右クリックします。
    1. プロパティの選択
    1. ダイアログボックスで、[リンカー-> 入力] を選択します。
    1. @No__t-0 を含むように追加の依存関係を更新します。 次に、例を示します。
        1. `windowscoreheadless.lib;%(...AdditionalDependencies...)`

![vsproj3](./images/vs_project3.png)
