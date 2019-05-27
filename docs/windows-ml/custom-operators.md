---
author: eliotcowley
title: カスタム演算子
description: このセクションには、カスタム演算子の Win32 Api のドキュメントが含まれています。
ms.author: elcowle
ms.date: 4/1/2019
ms.topic: article
keywords: windows 10、windows machine learning、WinML、カスタム演算子
ms.localizationpriority: medium
ms.openlocfilehash: 5f901b97f392278cad101b0581813cbcd32fcf80
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180894"
---
# <a name="custom-operators"></a>カスタム演算子

Win32 Api にある Windows Machine Learning カスタム演算子**MLOperatorAuthor.h**します。

## <a name="apis"></a>API

次にカスタム演算子の Api の構文と説明の一覧を示します。

### <a name="enumerations"></a>列挙

| 名前 | 説明 |
|------|-------------|
| [MLOperatorAttributeType](custom-operators/MLOperatorAttributeType.md) | 属性の型を指定します。 各属性の型には、対応する ONNX 型数値と一致します。 |
| [MLOperatorEdgeType](custom-operators/MLOperatorEdgeType.md) | 演算子のエッジを入力または出力の種類を指定します。 |
| [MLOperatorExecutionType](custom-operators/MLOperatorExecutionType.md) | カーネルが計算のため、CPU または GPU を使用するかどうかを指定します。 |
| [MLOperatorKernelOptions](custom-operators/MLOperatorKernelOptions.md) | カスタム演算子のカーネルを登録するときに使用するオプションを指定します。 |
| [MLOperatorParameterOptions](custom-operators/MLOperatorParameterOptions.md) | 演算子の入力と出力のオプション フラグを指定します。 |
| [MLOperatorSchemaEdgeTypeFormat](custom-operators/MLOperatorSchemaEdgeTypeFormat.md) | 入力と出力の種類でエッジが説明されている方法を指定します。 |
| [MLOperatorTensorDataType](custom-operators/MLOperatorTensorDataType.md) | 利用したテンソルのデータ型を指定します。 データの種類ごとには、対応する ONNX 型数値と一致します。 |

### <a name="functions"></a>関数

| 名前 | 説明 |
|------|-------------|
| [MLCreateOperatorRegistry](custom-operators/MLCreateOperatorRegistry.md) | インスタンスを作成します[IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md)カスタム演算子のカーネルとカスタム演算子のスキーマを登録するこれを使用することがあります。 |

### <a name="interfaces"></a>インターフェイス

| 名前 | 説明 |
|------|-------------|
| [IMLOperatorAttributes](custom-operators/IMLOperatorAttributes.md) | 演算子を使用して、モデルによって決定される、演算子の属性の値を表します。 |
| [IMLOperatorKernel](custom-operators/IMLOperatorKernel.md) | カスタム演算子カーネルによって実装されます。 |
| [IMLOperatorKernelContext](custom-operators/IMLOperatorKernelContext.md) | カーネルの計算中は、演算子の使用状況に関する情報を提供します。 |
| [IMLOperatorKernelCreationContext](custom-operators/IMLOperatorKernelCreationContext.md) | カーネルの作成中には、演算子の使用状況に関する情報を提供します。 |
| [IMLOperatorKernelFactory](custom-operators/IMLOperatorKernelFactory.md) | そのカーネルのインスタンスを作成するカスタム演算子のカーネルの作成者によって実装されます。 |
| [IMLOperatorRegistry](custom-operators/IMLOperatorRegistry.md) | カスタム演算子のカーネルとスキーマについてのレジストリのインスタンスを表します。 |
| [IMLOperatorShapeInferenceContext](custom-operators/IMLOperatorShapeInferenceContext.md) | 図形 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。 |
| [IMLOperatorShapeInferrer](custom-operators/IMLOperatorShapeInferrer.md) | 演算子の出力 tensor エッジの図形を推論する図形 inferrers によって実装されます。 |
| [IMLOperatorTensor](custom-operators/IMLOperatorTensor.md) | カスタム演算子のカーネルの計算中に使用される利用したテンソルの表現。 |
| [IMLOperatorTensorShapeDescription](custom-operators/IMLOperatorTensorShapeDescription.md) | 演算子の入力と出力の tensor 図形のセットを表します。 |
| [IMLOperatorTypeInferenceContext](custom-operators/IMLOperatorTypeInferenceContext.md) | 型 inferrers に呼び出されたときに、演算子の使用状況に関する情報を提供します。 |
| [IMLOperatorTypeInferrer](custom-operators/IMLOperatorTypeInferrer.md) | 型 inferrers によって実装される、演算子の型を推論する出力のエッジ。 |

### <a name="structures"></a>構造体

| 名前 | 説明 |
|------|-------------|
| [MLOperatorAttribute](custom-operators/MLOperatorAttribute.md) | カスタム演算子の属性のプロパティと名前を指定します。 |
| [MLOperatorAttributeNameValue](custom-operators/MLOperatorAttributeNameValue.md) | カスタム演算子の属性の値と名前を指定します。 |
| [MLOperatorEdgeDescription](custom-operators/MLOperatorEdgeDescription.md) | 演算子のエッジを入力または出力のプロパティを指定します。 |
| [MLOperatorEdgeTypeConstraint](custom-operators/MLOperatorEdgeTypeConstraint.md) | カスタム演算子のカーネルとスキーマでサポートされているエッジの種類に関連する制約を指定します。 |
| [MLOperatorKernelDescription](custom-operators/MLOperatorKernelDescription.md) | そのスキーマを登録するために使用するカスタム演算子カーネルの説明です。 |
| [MLOperatorSchemaDescription](custom-operators/MLOperatorSchemaDescription.md) | そのスキーマを登録に使用される演算子のカスタム スキーマの説明です。 |
| [MLOperatorSchemaEdgeDescription](custom-operators/MLOperatorSchemaEdgeDescription.md) | 演算子の入力または出力エッジに関する情報を指定します。 |
| [MLOperatorSetId](custom-operators/MLOperatorSetId.md) | 演算子セットの id を指定します。 |

[!INCLUDE [help](../includes/get-help.md)]
