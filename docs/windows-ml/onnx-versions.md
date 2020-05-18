---
title: ONNX バージョンと Windows ビルド
description: Windows 10 の各ビルドでサポートされている ONNX のバージョンを確認します。
ms.date: 5/13/2020
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning, ONNX
ms.localizationpriority: medium
ms.openlocfilehash: 24caa924ba7553d17712a6608e3a03555c29fcf7
ms.sourcegitcommit: 6a206c0965789ef4d2e1f8dfdd501971c108032a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83383624"
---
# <a name="onnx-versions-and-windows-builds"></a>ONNX バージョンと Windows ビルド

Windows Machine Learning は、リリースされている Windows ビルドで、特定のバージョンの ONNX 形式をサポートしています。 Windows ML でモデルを使用するには、アプリケーションの対象となる Windows リリースで、その ONNX モデルのバージョンがサポートされていることを確認する必要があります。

次の表は、現在リリースされているすべてのバージョンの Windows ML と、対応する ONNX のバージョンのサポート状況をまとめたものです。

| Windows のリリース | サポートされる ONNX バージョン | サポートされる ONNX opset |
|-----------------|-------------------------|-----------------------|
| Windows 10 バージョン 2004 (ビルド 19041) | 1.2.2、1.3、および 1.4 | 7、8、および 9 |
| Windows 10 バージョン 1909 | 1.2.2 および 1.3 | 7 および 8 |
| Windows 10 バージョン 1903 (ビルド 18362) | 1.2.2 および 1.3 | 7 および 8 |
| Windows 10 バージョン 1809 (ビルド 17763) | 1.2.2 | 7 |

Windows Insider フライト ビルドを使用して開発している場合、Windows 10 SDK のフライトでサポートされている ONNX の最小バージョンと最大バージョンについては[リリース ノート](release-notes.md) を確認してください。

## <a name="onnx-opset-converter"></a>ONNX opset コンバーター

ONNX API には、異なる opset バージョン間で ONNX モデルを変換するためのライブラリが用意されています。 これにより、開発者とデータ サイエンティストは、既存の ONNX モデルを新しいバージョンにアップグレードしたり、モデルを古いバージョンの ONNX 仕様にダウングレードしたりできます。

[バージョン コンバーター](https://github.com/onnx/onnx/blob/master/docs/VersionConverter.md)は、C++ または Python の API を使用して呼び出すことができます。 ONNX モデルを新しいターゲット opset にアップグレードおよびダウングレードする方法の例を示す[チュートリアル](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchToDifferentONNXOpsetVersions.md)も用意されています。

[!INCLUDE [help](../includes/get-help.md)]
