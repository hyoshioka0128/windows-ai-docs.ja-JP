---
author: eliotcowley
title: IMLOperatorKernelContext.GetOutputTensor method
description: 指定したインデックス位置にある演算子の出力 tensor を取得します。
ms.author: elcowle
ms.date: 4/1/2019
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
ms.openlocfilehash: 28b32a8061d0edfc7c466460d8080d800ff715ee
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66181204"
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

## <a name="requirements"></a>要件

| | |
|-|-|
| **最小のサポートされているクライアント** | Windows 10 ビルド 17763 |
| **最小のサポートされているサーバー** | デスクトップ エクスペリエンス搭載の Windows Server 2019 |
| **ヘッダー** | MLOperatorAuthor.h |

[!INCLUDE [help](../../includes/get-help.md)]
