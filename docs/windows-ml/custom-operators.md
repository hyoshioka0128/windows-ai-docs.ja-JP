---
title: カスタム演算子
description: このセクションには、カスタム演算子 Win32 Api のドキュメントが含まれています。
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子
ms.localizationpriority: medium
ms.openlocfilehash: 188d6aa5000f60954b91a980dc02d500557c2d90
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70157061"
---
# <a name="custom-operators"></a>カスタム演算子

Windows Machine Learning カスタム演算子の Win32 Api は、 **Mloperatorauthor. h**にあります。

## <a name="apis"></a>API

カスタム演算子 Api とその構文および説明を次に示します。

### <a name="enumerations"></a>列挙

| 名前 | 説明 |
|------|-------------|
| [MLOperatorAttributeType](custom-operators/MLOperatorAttributeType.md) | 属性の型を指定します。 各属性の型は、対応する ONNX 型に一致します。 |
| [MLOperatorEdgeType](custom-operators/MLOperatorEdgeType.md) | 演算子の入力または出力エッジの種類を指定します。 |
| [MLOperatorExecutionType](custom-operators/MLOperatorExecutionType.md) | カーネルが計算に CPU と GPU のどちらを使用するかを指定します。 |
| [MLOperatorKernelOptions](custom-operators/MLOperatorKernelOptions.md) | カスタム演算子カーネルを登録するときに使用するオプションを指定します。 |
| [MLOperatorParameterOptions](custom-operators/MLOperatorParameterOptions.md) | 入力および出力の演算子のエッジのオプションフラグを指定します。 |
| [MLOperatorSchemaEdgeTypeFormat](custom-operators/MLOperatorSchemaEdgeTypeFormat.md) | 入力と出力のエッジの種類を記述する方法を指定します。 |
| [MLOperatorTensorDataType](custom-operators/MLOperatorTensorDataType.md) | のデータ型を指定します。 それぞれのデータ型は、対応する ONNX 型に一致します。 |

### <a name="functions"></a>関数

| 名前 | 説明 |
|------|-------------|
| [MLCreateOperatorRegistry](custom-operators/MLCreateOperatorRegistry.md) | カスタム演算子カーネルとカスタムの演算子スキーマを登録するために使用できる[Imloperatorregistry](custom-operators/IMLOperatorRegistry.md)のインスタンスを作成します。 |

### <a name="interfaces"></a>インターフェイス

| 名前 | 説明 |
|------|-------------|
| [IMLOperatorAttributes](custom-operators/IMLOperatorAttributes.md) | 演算子を使用したモデルによって決定される、演算子の属性の値を表します。 |
| [IMLOperatorKernel](custom-operators/IMLOperatorKernel.md) | カスタム演算子カーネルによって実装されます。 |
| [IMLOperatorKernelContext](custom-operators/IMLOperatorKernelContext.md) | カーネルが計算されているときのオペレーターの使用状況に関する情報を提供します。 |
| [IMLOperatorKernelCreationContext](custom-operators/IMLOperatorKernelCreationContext.md) | カーネルの作成中にオペレーターの使用状況に関する情報を提供します。 |
| [IMLOperatorKernelFactory](custom-operators/IMLOperatorKernelFactory.md) | カスタムオペレータカーネルの作成者によって実装され、そのカーネルのインスタンスを作成します。 |
| [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md) | カスタム演算子カーネルおよびスキーマのレジストリのインスタンスを表します。 |
| [IMLOperatorShapeInferenceContext](custom-operators/IMLOperatorShapeInferenceContext.md) | 図形が呼び出されている間に、演算子の使用法に関する情報を提供します。 |
| [IMLOperatorShapeInferrer](custom-operators/IMLOperatorShapeInferrer.md) | 図形形式で実装され、演算子の出力の形状を推定します。 |
| [IMLOperatorTensor](custom-operators/IMLOperatorTensor.md) | カスタム演算子カーネルの計算中に使用される、オートの表現。 |
| [IMLOperatorTensorShapeDescription](custom-operators/IMLOperatorTensorShapeDescription.md) | オペレーターの入力および出力のセットを表します。 |
| [IMLOperatorTypeInferenceContext](custom-operators/IMLOperatorTypeInferenceContext.md) | 型 inferrers の呼び出し中に、演算子の使用法に関する情報を提供します。 |
| [IMLOperatorTypeInferrer](custom-operators/IMLOperatorTypeInferrer.md) | 演算子の出力エッジの型を推論するために型 inferrers によって実装されます。 |

### <a name="structures"></a>構造体

| 名前 | 説明 |
|------|-------------|
| [MLOperatorAttribute](custom-operators/MLOperatorAttribute.md) | カスタム演算子の属性の名前とプロパティを指定します。 |
| [MLOperatorAttributeNameValue](custom-operators/MLOperatorAttributeNameValue.md) | カスタム演算子の属性の名前と値を指定します。 |
| [MLOperatorEdgeDescription](custom-operators/MLOperatorEdgeDescription.md) | 演算子の入力または出力エッジのプロパティを指定します。 |
| [MLOperatorEdgeTypeConstraint](custom-operators/MLOperatorEdgeTypeConstraint.md) | カスタム演算子カーネルおよびスキーマでサポートされているエッジの種類に対する制約を指定します。 |
| [MLOperatorKernelDescription](custom-operators/MLOperatorKernelDescription.md) | スキーマを登録するために使用されるカスタムオペレーターカーネルの説明。 |
| [MLOperatorSchemaDescription](custom-operators/MLOperatorSchemaDescription.md) | スキーマの登録に使用されるカスタムオペレータースキーマの説明です。 |
| [MLOperatorSchemaEdgeDescription](custom-operators/MLOperatorSchemaEdgeDescription.md) | 演算子の入力または出力エッジに関する情報を指定します。 |
| [MLOperatorSetId](custom-operators/MLOperatorSetId.md) | オペレーターセットの id を指定します。 |

[!INCLUDE [help](../includes/get-help.md)]
