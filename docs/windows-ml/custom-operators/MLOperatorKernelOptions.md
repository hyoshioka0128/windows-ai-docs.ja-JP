---
title: MLOperatorKernelOptions 列挙型
description: カスタム演算子カーネルを登録するときに使用するオプションを指定します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、MLOperatorKernelOptions
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- MLOperatorKernelOptions
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: f1e1cf8bd3313f1fc64b90901a5bfd002f1c68a0
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157719"
---
# <a name="mloperatorkerneloptions-enum"></a>MLOperatorKernelOptions 列挙型

カスタム演算子カーネルを登録するときに使用するオプションを指定します。

## <a name="fields"></a>フィールド

| 名前 | 値 | 説明 |
|------|-------|-------------|
| なし | 0 | |
| AllowDynamicInputShapes | 1 | 入力 tensors の図形がオペレーターカーネルインスタンスの呼び出し間で異なることを許可するかどうかを指定します。 これが設定されていない場合、カーネルインスタンスは、作成中に入力された入力や図形を照会したり、これらの図形に依存するフロントロード初期化作業を実行したりすることができます。 これを設定すると、推論操作の間に図形が動的に変化し、カーネル実装がこれを効率的に処理する場合に、パフォーマンスが向上する可能性があります。 |

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
