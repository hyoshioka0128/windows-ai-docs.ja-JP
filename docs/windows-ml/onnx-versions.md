---
title: ONNX バージョンと Windows ビルド
description: 各 Windows 10 ビルドでサポートされている ONNX のバージョンを確認します。
ms.date: 7/2/2019
ms.topic: article
keywords: windows 10、windows ai、windows ml、winml、windows machine learning、onnx
ms.localizationpriority: medium
ms.openlocfilehash: 0124f1a5d66a2b8801aaab10237ed731faddf44f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156362"
---
# <a name="onnx-versions-and-windows-builds"></a>ONNX バージョンと Windows ビルド

Windows Machine Learning は、リリースされた Windows ビルドで ONNX 形式の特定のバージョンをサポートしています。 Windows ML でモデルを使用するには、アプリケーションの対象となる Windows リリースで ONNX モデルバージョンがサポートされていることを確認する必要があります。

次の表は、現在リリースされているすべてのバージョンの Windows ML とそれに対応する ONNX のバージョンをまとめたものです。

| Windows のリリース | サポートされている ONNX のバージョン | サポートされている ONNX opsets |
|-----------------|-------------------------|-----------------------|
| Windows 10 バージョン 1903 (ビルド 18362) | 1.2.2 と1.3 | 7と8 |
| Windows 10 バージョン 1809 (ビルド 17763) | 1.2.2 | 7 |

Windows Insider フライトビルドを使用して開発している場合は、Windows 10 SDK のフライトでサポートされている ONNX の最小バージョンと最大バージョンについて、[リリースノート](release-notes.md)を確認してください。

## <a name="onnx-opset-converter"></a>ONNX opset コンバーター

ONNX API には、異なる opset バージョン間で ONNX モデルを変換するためのライブラリが用意されています。 これにより、開発者とデータ科学者は、既存の ONNX モデルを新しいバージョンにアップグレードしたり、モデルを古いバージョンの ONNX 仕様にダウングレードしたりすることができます。

[バージョンコンバーターは、](https://github.com/onnx/onnx/blob/master/docs/VersionConverter.md)または Python api C++を使用して呼び出すことができます。 また、ONNX モデルを新しいターゲット opset にアップグレードおよびダウングレードする方法について、いくつかの例を示した[チュートリアル](https://github.com/onnx/tutorials/blob/master/tutorials/ExportModelFromPyTorchToDifferentONNXOpsetVersions.md)もあります。

[!INCLUDE [help](../includes/get-help.md)]
