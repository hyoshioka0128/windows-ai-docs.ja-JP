---
title: Azure IoT Edge ランタイム
description: Azure IoT Edge を使用してデバイスに Windows ML コンテナーを追加する方法について説明します
ms.date: 10/14/2019
ms.topic: article
keywords: windows 10、windows ml コンテナー、コンテナー、iot、エッジ
ms.localizationpriority: medium
ms.openlocfilehash: 4c8f327505216321a0ff5a1939e25d4fba6a8cf2
ms.sourcegitcommit: f5945af6d1f534b490eea7860f72804dc1c9fea8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315406"
---
# <a name="use-the-windows-ml-container-insider-preview-with-azure-iot-edge-runtime"></a>Azure IoT Edge ランタイムで Windows ML コンテナー Insider Preview を使用する

ホスト OS とコンテナーバージョンの一致要件により、Windows ML コンテナー Insider Preview で Azure IoT Edge ランタイムを使用するには、Azure IoT Edge ランタイム環境を準備するために必要ないくつかの手順を実行します。  

> [!IMPORTANT]
> 次の手順では、 [Docker](https://docs.docker.com/engine/reference/commandline/cli/)と[Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/)の使用経験があることを前提としています。

## <a name="environment-setup"></a>環境のセットアップ

インストールされている Windows ML コンテナーと一致するバージョンの Windows Insider Preview ホストコンピューターで、次の操作を行います。
- [.NET Core SDK をインストール](https://dotnet.microsoft.com/download)します。
- [Git をインストール](https://git-scm.com/downloads)します。
- 「[作業の開始](getting-started.md)」の手順に従って、docker マスターから docker をインストールします。
- [Azure CLI をインストール](https://docs.microsoft.com/cli/azure/install-azure-cli-windows?view=azure-cli-latest)します。
- Azure IoT Edge モジュールを格納するために Azure Container Registry に[プライベートコンテナーレジストリを作成](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal)します。 ([管理者アカウント](https://docs.microsoft.com/azure/container-registry/container-registry-authentication)が有効になっていると、ログインが簡単になる場合があることに注意してください)。
- クラウド上のデバイスと展開を管理するための[Azure IoT Hub を作成](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-create-through-portal)します。

## <a name="build-private-azure-iot-edge-runtime-module"></a>プライベート Azure IoT Edge ランタイムモジュールをビルドする

### <a name="prepare-base-os-image"></a>基本 OS イメージの準備

- 管理者として CMD または powershell を起動します。
- Docker から Azure Container Registry にログインします。
- Windows ML コンテナーの基本イメージ*をプルする (Insider ホストのバージョンに合わせてタグを変更する*) には、次のコマンドを使用します。
    - `docker pull mcr.microsoft.com/windows/ml/insider:10.0.18999.1`
    - `docker tag mcr.microsoft.com/windows/ml/insider:10.0.18999.1 windowsml:latest`
- Azure IoT Edge を `C:\iotedge` に複製します。
    - `cd /d c:\`
    - `git clone https://github.com/Azure/iotedge.git`

### <a name="build-edge-hub-container"></a>エッジハブコンテナーの構築

次のコマンドを実行して、Edge ハブコンテナーを構築します。

- `cd c:\iotedge\edge-hub\src\Microsoft.Azure.Devices.Edge.Hub.Service\`
- `dotnet publish -r win-x64`
- `cd bin\Debug\netcoreapp2.1\win-x64\`

- 次のようなコンテンツを含む Dockerfile を作成し @no__t 0 に保存します。

    ```console
    FROM windowsml:latest
    WORKDIR /app
    COPY publish/ ./
    # Expose MQTT, AMQP and HTTPS ports-
    EXPOSE 8883/tcp
    EXPOSE 5671/tcp
    EXPOSE 443/tcp
    CMD ["Microsoft.Azure.Devices.Edge.Hub.Service.exe"]
    ```

    次のコマンドを使用して続行します。

    - `docker build . -t your-own-registry.azurecr.io/hub:latest`
    - `docker push your-own-registry.azurecr.io/hub:latest`

### <a name="build-agent-container"></a>ビルドエージェントコンテナー

次のコマンドを実行して、エージェントコンテナーをビルドします。

- `cd c:\iotedge\edge-agent\src\Microsoft.Azure.Devices.Edge.Agent.Service\`
- `dotnet publish -r win-x64`
- `cd bin\Debug\netcoreapp2.1\win-x64`

- 次のようなコンテンツを含む Dockerfile を作成し、に保存します。 `c:\iotedge\edge-agent\src\Microsoft.Azure.Devices.Edge.Agent.Service\bin\Debug\netcoreapp2.1\win-x64`
    ```console
    FROM windowsml:latest
    # Configure web servers to bind to port 80 when present
    ENV ASPNETCORE_URLS=http://+:80
    WORKDIR /app
    COPY publish/ ./
    CMD ["Microsoft.Azure.Devices.Edge.Agent.Service.exe"]
    ```

次のコマンドを使用して続行します。

- `docker build . -t your-own-registry.azurecr.io/agent:latest`
- `docker push your-own-registry.azurecr.io/agent:latest`

### <a name="build-other-azure-iot-edge-modules"></a>その他の Azure IoT Edge モジュールをビルドする

Windows Insider host で Azure IoT Edge および Windows ML Insider Preview コンテナーを実行している Edge デバイスに他のモジュールが展開される場合は、それらのモジュールを再構築する必要があります。これらのモジュールは、Windows Insider ホストのバージョン。

## <a name="configure-iot-edge-in-the-azure-iot-hub-portal"></a>Azure IoT Hub ポータルでの IoT Edge の構成

- Azure IoT Hub に IoT Edge デバイスを作成します。
    ![iotedge01 @ no__t-1

- デバイスに**Testdevice**という名前を指定し、[対称キー] を選択します。
    ![iotedge02 @ no__t-1

- **[モジュールの設定]** を選択します。
    ![iotedge03 @ no__t-1

- プライベートに構築されたモジュールがプッシュされたコンテナーレジストリの詳細を指定します。
    ![iotedge04 @ no__t-1

- [Set Modules] \ (モジュールの設定 \) ページの [edge**ランタイム設定の構成**] ボタンをクリックし、[edge Hub] と [edge エージェント] を、プライベートコンテナーを発行した場所に設定します。
    ![iotedge05 @ no__t-1

- **[保存]** ボタンを選択します。
- 忘れずに次の **>** を選択してください。

この時点から、必要に応じていくつかのデプロイモジュールをデバイスに追加できます。

## <a name="setting-up-azure-iot-edge-on-windows-ml-container-host"></a>Windows ML コンテナーホストでの Azure IoT Edge の設定

> [!IMPORTANT]
> Azure IoT Edge を設定するときは、コンテナー OS のバージョンが、Edge ハブおよび Edge エージェントモジュールのビルドに使用されたコンテナーホストのバージョンと一致していることを確認してください。

- IoT Edge がインストールされているデバイスは、Docker を実行していてはなり**ません**。
- 上記のコンテナービルドコンピューターを試している場合は、Docker サービスを停止して無効にすることができます。

### <a name="download-and-modify-installation-powershell-script"></a>インストール powershell スクリプトをダウンロードして変更する

- @No__t-0 のコピーをローカルに保存します。このコマンドは、*管理者特権*のプロンプトから実行します。

```console
curl -o c:\IotEdgeSecurityDaemon.ps1 -L  https://raw.githubusercontent.com/Azure/iotedge/1.0.8/scripts/windows/setup/IotEdgeSecurityDaemon.ps1
```

- @No__t-0 を変更してビルドバージョンの制約を無効にする
-   @No__t-0 関数で、次の行をコメントアウトします。

```console
 #   if (-not (Setup-Environment -ContainerOs $ContainerOs -SkipArchCheck -SkipBatteryCheck)) {
 #       return
 #   }
```
-   @No__t-0 関数で、次の行をコメントアウトします。

```console
#    if (-not (Setup-Environment -ContainerOs $ContainerOs -SkipArchCheck:$SkipArchCheck -SkipBatteryCheck:$SkipBatteryCheck)) {
#        return
#    }
```

### <a name="install-iot-edge"></a>IoT Edge のインストール

- *管理者特権*の PowerShell インスタンスから次のコマンドを実行します。

```console
. {Invoke-WebRequest -useb c:\IotEdgeSecurityDaemon.ps1} | Invoke-Expression;  Deploy-IoTEdge
```

- デバイスが再起動された場合は、再起動されるのを待ちます。 必要に応じて、*管理者特権*の PowerShell インスタンスをもう一度起動し、次のコマンドを実行します。

> [!NOTE]
> 次の例では、コンテナーレジストリ、ユーザー名、パスワード、および接続文字列を必ず置き換えてください。

```console
. {Invoke-WebRequest -useb c:\IotEdgeSecurityDaemon.ps1} | Invoke-Expression; Initialize-IoTEdge -AgentImage your-container-registry.azurecr.io/agent:latest  -Username yourRegistryUserName -Password $(ConvertTo-SecureString yourregistryPassword -AsPlainText -Force)  -Manual -DeviceConnectionString connectionstringOfTestDevice
```

- プロセスが終了するまで数分待ってから、次のコマンドを実行します。

```console
PS C:\> iotedge list
```

次に示すように、エージェントとハブが実行されていることを確認できます。

```
NAME             STATUS           DESCRIPTION      CONFIG
edgeHub          running          Up 9 seconds     winmlc.azurecr.io/hub:latest
edgeAgent        running          Up 22 seconds    winmlc.azurecr.io/agent:latest
```
