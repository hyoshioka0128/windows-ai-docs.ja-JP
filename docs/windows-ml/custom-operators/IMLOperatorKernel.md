---
title: IMLOperatorKernel インターフェイス
description: カスタム演算子カーネルによって実装されます。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、IMLOperatorKernel
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernel
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: b00ced7748b55f8153c346c7e5f2c1083cb18bfd
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157099"
---
# <a name="imloperatorkernel-interface"></a>IMLOperatorKernel インターフェイス

カスタム演算子カーネルによって実装されます。 [Imloperatorregistry:: Registeroperator kernel](IMLOperatorRegistry_RegisterOperatorKernel.md)を使用してカスタム演算子カーネルを登録するときに、このインターフェイスのインスタンスを作成するファクトリが提供されます。

## <a name="methods"></a>メソッド

| 名前 | 説明 |
|------|-------------|
| [Compute](IMLOperatorKernel_Compute.md) | カーネルの出力を計算します。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
