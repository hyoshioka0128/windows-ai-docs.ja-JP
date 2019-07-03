---
author: eliotcowley
title: ONNX バージョンと Windows のビルド
description: サポートされている ONNX のバージョンを確認、各 Windows 10 ビルドします。
ms.author: elcowle
ms.date: 7/2/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows machine learning、onnx
ms.localizationpriority: medium
ms.openlocfilehash: 46a98f886fdd31002bf30023a534b10ac3a3bec4
ms.sourcegitcommit: 8c18dfc753694e26067e3155509cf6d7c970a765
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515721"
---
# <a name="onnx-versions-and-windows-builds"></a>ONNX バージョンと Windows のビルド

Windows Machine Learning では、Windows のリリースのビルドに ONNX 形式の特定のバージョンをサポートしています。 Windows の ML を使用するモデルの順番 ONNX モデルのバージョンは、Windows のリリースでサポートされていることを確認する必要があります、アプリケーションの対象とします。

次の表には、すべての現在リリースされているバージョンの Windows の ML とサポートされている対応する ONNX バージョンをまとめたものです。

| Windows のリリース | サポートされている ONNX バージョン | サポートされている ONNX opsets |
|-----------------|-------------------------|-----------------------|
| Windows 10 バージョン 1903 (18362 をビルドする) | 1.2.2 1.3 | 7 および 8 |
| Windows 10 バージョン 1809 (17763 をビルドする) | 1.2.2 | 7 |

Windows Insider のフライトのビルドを使用して開発する場合を確認してください、[リリース ノート](release-notes.md)最小値と最大値には、Windows 10 SDK のフライト ONNX バージョンがサポートされています。

## <a name="onnx-opset-converter"></a>ONNX opset コンバーター

ONNX API は、異なる opset バージョン間で ONNX モデルを変換するため、ライブラリを提供します。 これにより、開発者やデータ サイエンティストを新しいバージョンでは、既存の ONNX モデルをアップグレードするか、モデル、ONNX 仕様の以前のバージョンをダウン グレードできます。

[バージョン コンバーター](https://github.com/onnx/onnx/blob/master/docs/VersionConverter.md)可能性がありますいずれかによって呼び出されるC++または Python Api です。 [チュートリアル](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchToDifferentONNXOpsetVersions.md)アップグレードや、新しいターゲット opset ONNX モデルをダウン グレードする方法のいくつかの例を提供します。

[!INCLUDE [help](../includes/get-help.md)]
