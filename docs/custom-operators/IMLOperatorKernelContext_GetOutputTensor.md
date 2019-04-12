---
author: eliotcowley
title: IMLOperatorKernelContext.GetOutputTensor method
description: 指定したインデックス位置にある演算子の出力 tensor を取得します。
ms.author: elcowle
ms.date: 11/8/2018
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子を GetOutputTensor
ms.localizationpriority: medium
topic_type:
- APIRef
api_type:
- NA
api_name:
- IMLOperatorKernelContext.GetOutputTensor
api_location:
- MLOperatorAuthor.h
ms.openlocfilehash: 0c0f708acfad55a1d4d7d8fe33b81da9f7289e42
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474869"
---
# <a name="imloperatorkernelcontextgetoutputtensor-method"></a>IMLOperatorKernelContext.GetOutputTensor method

## <a name="overloads"></a>オーバー ロード

| | |
|-|-|
| [GetOutputTensor(uint32_t, IMLOperatorTensor**)](#GetOutputTensor1) | 指定したインデックス位置にある演算子の出力 tensor を取得します。 |
| [GetOutputTensor(uint32_t, uint32_t, const uint32_t*, IMLOperatorTensor**)](#GetOutputTensor2) | 指定したインデックス位置の形状を宣言するときに、演算子の出力 tensor を取得します。 |

<a name="GetOutputTensor1"></a>
## <a name="getoutputtensoruint32t-imloperatortensor"></a>GetOutputTensor(uint32_t, IMLOperatorTensor**)

指定したインデックス位置にある演算子の出力 tensor を取得します。 これにより、利用したテンソルに設定**nullptr**存在しない出力の省略可能です。 演算子のカーネルが図形の推論メソッドでは、次のオーバー ロードすることがなく登録された場合**GetOutputTensor** tensor の図形を使用し、代わりに呼び出す必要があります。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
void GetOutputTensor(
    uint32_t outputIndex, 
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

<a name="GetOutputTensor2"></a>
## <a name="getoutputtensoruint32t-uint32t-const-uint32t-imloperatortensor"></a>GetOutputTensor(uint32_t, uint32_t, const uint32_t*, IMLOperatorTensor**)

指定したインデックス位置の形状を宣言するときに、演算子の出力 tensor を取得します。 返されます。 **nullptr**存在しない出力の省略可能です。 演算子のカーネルが、図形の推論メソッドのオーバー ロードに登録された場合**GetOutputTensor**図形を使用しない場合があります呼び出すこともできます。 指定したインデックス位置の出力を利用したテンソルでない場合は、エラーを返します。

```cpp
void GetOutputTensor(
    uint32_t outputIndex,
    uint32_t dimensionCount,
    _In_reads_(dimensionCount) const uint32_t* dimensionSizes,
    _COM_Outptr_result_maybenull_ IMLOperatorTensor** tensor)
```

## <a name="requirements"></a>必要条件

| | |
|-|-|
| **サポートされている最小のクライアント** | Windows 10 ビルド 17763 |
| **サポートされている最小のサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **Header** | MLOperatorAuthor.h |

[!INCLUDE [help](../includes/get-help.md)]
