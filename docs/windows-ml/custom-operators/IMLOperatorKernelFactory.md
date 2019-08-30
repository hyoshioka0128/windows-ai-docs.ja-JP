---
title: Imloperatorのインターフェイス
description: カスタムオペレータカーネルの作成者によって実装され、そのカーネルのインスタンスを作成します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Imloperator・ Factory
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelFactory
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 67943742b596426512772a39c41ba42250131e1f
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157597"
---
# <a name="imloperatorkernelfactory-interface"></a>Imloperatorのインターフェイス

カスタムオペレータカーネルの作成者によって実装され、そのカーネルのインスタンスを作成します。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [CreateKernel](IMLOperatorKernelFactory_CreateKernel.md) | 指定されたコンテキストオブジェクトに記述されているモデル内の演算子の使用法に関する情報を指定して、関連付けられている演算子カーネルのインスタンスを作成します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
