---
title: Imloperatoro Context. Getoutputのメソッド
description: 指定したインデックス位置にある演算子によって取得された出力を取得します。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子、Getoutputは、
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetOutputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 3755c292420d858ebef696fd422bb8b705809d0c
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157294"
---
# <a name="imloperatorkernelcontextgetoutputtensor-method"></a>Imloperatoro Context. Getoutputのメソッド

## <a name="overloads"></a>Overloads

| | |
|-|-|
| [Getoutputuint32_t (または、Imloperator、* *)](#GetOutputTensor1) | 指定したインデックス位置にある演算子によって取得された出力を取得します。 |
| [Getoutputuint32_t (uint32_t、const uint32_t *、Imloperatorall * *)](#GetOutputTensor2) | 図形の宣言中に、指定したインデックス位置にある演算子によって取得された出力を取得します。 |

<a name="GetOutputTensor1"></a>
## <a name="getoutputtensoruint32_t-imloperatortensor"></a>GetOutputTensor(uint32_t, IMLOperatorTensor**)

指定したインデックス位置にある演算子によって取得された出力を取得します。 これにより、存在しない省略可能な出力に対して、このオプションが**nullptr**に設定されます。 演算子カーネルが図形の推定メソッドを使用せずに登録されている場合は、代わりに、その形状を使用する**Getoutputの**オーバーロードを呼び出す必要があります。 指定されたインデックスの出力が、まだ存在しない場合はエラーを返します。

```cpp
void GetOutputTensor(
    uint32_t outputIndex,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

<a name="GetOutputTensor2"></a>
## <a name="getoutputtensoruint32_t-uint32_t-const-uint32_t-imloperatortensor"></a>GetOutputTensor(uint32_t, uint32_t, const uint32_t*, IMLOperatorTensor**)

図形の宣言中に、指定したインデックス位置にある演算子によって取得された出力を取得します。 これは、存在しないオプションの出力に対して**nullptr**を返します。 演算子カーネルが図形の推定メソッドに登録されている場合は、図形を使用しない**Getoutputの**オーバーロードが呼び出されることもあります。 指定されたインデックスの出力が、まだ存在しない場合はエラーを返します。

```cpp
void GetOutputTensor(
    uint32_t outputIndex,
    uint32_t dimensionCount,
    _In_reads_(dimensionCount) const uint32_t* dimensionSizes,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>要件

| | |
|-|-|
| **サポートされている最低限のクライアント** | Windows 10、ビルド17763 |
| **サポートされている最小サーバー** | デスクトップエクスペリエンスを備えた Windows Server 2019 |
| **項目** | MLOperatorAuthor. h |

[!INCLUDE [help](../../includes/get-help.md)]
