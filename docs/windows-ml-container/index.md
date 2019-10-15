---
title: Windows ML コンテナーの Insider Preview
description: Windows ML コンテナーを使用して、機械学習を IoT デバイスに追加する
ms.date: 10/14/2019
ms.topic: article
keywords: windows 10, windows ml container, container, iot, edge
ms.localizationpriority: medium
ms.openlocfilehash: aee749d7aa77a48a6559d5dcd183926dfa86cd3c
ms.sourcegitcommit: f5945af6d1f534b490eea7860f72804dc1c9fea8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315376"
---
# <a name="windows-ml-container-insider-preview"></a>Windows ML コンテナーの Insider Preview

高パフォーマンス API セットである [Windows ML](https://docs.microsoft.com/windows/ai/windows-ml/) は、標準 [ONNX モデル](https://docs.microsoft.com/windows/ai/windows-ml/get-onnx-model)を使用して Windows 上での ML 推論を実現します。  多くの場合、Machine Learning では、多大なコンピューティング能力が必要となります。 Windows ML の主な利点の 1 つとして、これは、すべての DirectX12 準拠の GPU または Microsoft Compute Driver Model 準拠の ASIC を使用してハードウェア アクセラレータによる計算を高速化するため、アクセシビリティが高まります。

Windows ML コンテナーは、Windows ML API を利用するワークロードをコンテナー化するように特別に設計された新しい Windows コンテナーです。 また、バスでのセンサーまたは USB カメラ (USB、I2C、SPI、GPIO など) などの周辺機器への直接アクセスも提供します。 これらのワークロード専用にコンテナーを最適化することで、コンテナーのディスク上のサイズを約 350 MB にまで減らすことができます。 これは、ハードウェア アクセラレータによる ML 推論機能を持つ他のすべてのコンテナーに比べ大幅に小さい数値です。  

![Windows ML コンテナー](./images/winmlcontainer.png)

Windows ML コンテナーを使用すると、高速かつ機動性のあるプラットフォームを使って、エンタープライズレベルの IoT ソリューションを構築できます。 Windows の高度な機能、Windows 10 IoT プラットフォームのセキュリティ、Azure IoT Edge サービスの管理容易性を兼ね備えています。

## <a name="getting-started"></a>概要

Windows ML コンテナーの使用を検討していますか。 詳細については、「[作業の開始](getting-started.md)」を参照してください。

## <a name="supported-apis"></a>サポートされる API

Windows ML コンテナーは、C++、C#、NET Core、Node.JS、Python など、さまざまな言語およびフレームワークで記述されたワークロードをサポートしています。 ただし、パフォーマンスとサイズの最適化により、Windows ML コンテナーでサポートされる OS API サーフェスは、完全な Windows コンテナーよりも小さくなっています。 多くのユーザー インターフェイス API と高レベルの UWP API は、コンテナーで実行されるワークロードでは利用できません。 サポートされる API には、OneCore API サーフェスの API、デバイス アクセスをサポートするための WinRT コントラクト、Windows ML API などが含まれます。

サポートされる API とコントラクトの詳細な一覧については、[サポートされている API の一覧](api-list.md)をご覧ください。

## <a name="feedback"></a>Feedback

フィードバックをお聞かせください。

今回も、皆様からの貴重なご意見をお待ちしております。 ご意見やご感想を winmlcfb@microsoft.com までお寄せください。
