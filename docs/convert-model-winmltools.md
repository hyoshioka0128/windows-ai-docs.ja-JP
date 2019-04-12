---
author: wschin
title: ML モデルを WinMLTools で ONNX に変換します。
description: WinMLTools を使用して ML モデルを ONNX 形式に変換する方法について説明します。
ms.author: wechi
ms.date: 11/7/2018
ms.topic: article
keywords: windows 10、windows の machine learning、WinML、WinMLTools、ONNX、ONNXMLTools、scikit、学習、Core ML、Keras
ms.localizationpriority: medium
ms.openlocfilehash: 123879f5f7ec43b68e6b69db9af1829c22534302
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59475029"
---
# <a name="convert-ml-models-to-onnx-with-winmltools"></a>ML モデルを WinMLTools で ONNX に変換します。

[WinMLTools](https://pypi.org/project/winmltools/) ONNX にさまざまなトレーニング フレームワークで作成された ML モデルを変換することができます。 拡張機能は[ONNXMLTools](https://github.com/onnx/onnxmltools)と[TF2ONNX](https://github.com/onnx/tensorflow-onnx) Windows ML で使用するために ONNX モデルを変換します。 

現在、WinMLTools には、次のフレームワークからの変換がサポートされています。

- Apple CoreML
- Keras
- scikit、について説明します
- lightgbm
- xgboost
- libSVM
- Tensorflow (試験段階)


その他の ML フレームワークからエクスポートする方法についてを参照してください[ONNX チュートリアル](https://github.com/onnx/tutorials)GitHub でします。

この記事に WinMLTools を使用する方法について説明します。

- ONNX CoreML モデルに変換します。
- 変換 scikit-に ONNX モデルを説明します。
- Tensorflow モデルを ONNX に変換します。
- 量子化した ONNX モデルを onnx モデルに変換します。
- 16 ビットの浮動小数点モデル精度のモデルをポイントする浮動小数点を変換します。
- カスタムの ONNX オペレーターを作成します。

>[!NOTE]
>[WinMLTools の最新バージョン](https://pypi.org/project/winmltools/1.3.0/)ONNX opsets 7 と 8 でそれぞれ指定された ONNX バージョン 1.2.2 および 1.3 への変換をサポートしています。 ツールの以前のバージョンでは、ONNX 1.3 のサポートはありません。

## <a name="install-winmltools"></a>WinMLTools のインストール

WinMLTools は、Python バージョン 2.7 および 3.6 をサポートする Python パッケージ (winmltools) です。 データ サイエンス プロジェクトを扱う場合は、Anaconda などのサイエンス向けの Python ディストリビューションをインストールすることをお勧めします。

> [!NOTE]
> WinMLTools は、Python 3.7 を現在サポートしていません。

WinMLTools は、[Python パッケージの標準のインストール手順](https://packaging.python.org/installing/)に従っています。 Python 環境から次のコマンドを実行します。

```console
pip install winmltools
```

WinMLTools には次の依存関係があります。

- numpy v1.10.0 以降
- protobuf v.3.6.0+
- onnx v1.3.0 +
- onnxmltools v1.3.0 +
- tf2onnx v0.3.2+

依存パッケージを更新するには、pip コマンドに '-U' 引数を付けて実行してください。

```console
pip install -U winmltools
```

別のコンバーターの変換で異なるパッケージをインストールする必要

Libsvm、さまざまな web ソースから libsvm ホイールをダウンロードすることができます。 1 つの例はここにあります。 https://www.lfd.uci.edu/~gohlke/pythonlibs/#libsvm

Coremltools、現在 coreml は windows 上の coreml パッケージを配布しません。 ソースからインストールすることができます。

    pip install git+https://github.com/apple/coremltools


onnxmltools の依存関係について詳しくは、GitHub の [onnxmltools](https://github.com/onnx/onnxmltools) をご覧ください。

WinMLTools の使い方について詳しくは、ヘルプ機能でパッケージ固有のドキュメントをご覧ください。

```console
help(winmltools)
```

## <a name="convert-coreml-models"></a>CoreML モデルに変換します。

ここでは、サンプルの Core ML モデル ファイルのパスが *example.mlmodel* であると想定します。

~~~python
from coremltools.models.utils import load_spec
# Load model file
model_coreml = load_spec('example.mlmodel')
from winmltools import convert_coreml
# Convert it!
# The automatic code generator (mlgen) uses the name parameter to generate class names.
model_onnx = convert_coreml(model_coreml, 7, name='ExampleModel')   
~~~

> [!NOTE]
>Convert_coreml() への呼び出しでは、2 番目のパラメーターは、target_opset し、参照、演算子のバージョン番号を既定の名前空間 ai.onnx します。 これらの演算子の詳細を参照してください[ここ](https://github.com/onnx/onnx/blob/master/docs/Operators.md)します。 このパラメーターは WinMLTools、異なる ONNX (現在 1.2.2 および 1.3 のバージョンはサポートされているバージョン) を対象とする開発者の最新バージョンで利用できます。 Windows で実行するモデルに変換する 10 年 2018年 10 月の更新、target_opset 7 (ONNX v1.2.2) を使用します。 Windows 10 Insider Preview ビルド 17763 より大きい、WinML は target_opset 7 および 8 (ONNX v.1.3) を使用したモデルを受け入れます。 [リリース ノート](release-notes.md)セクションには、さまざまなビルドでサポートされている WindowsML min と max ONNX バージョンも含まれています。


`model_onnx` は ONNX の [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176) オブジェクトです。 これは 2 つの異なる形式で保存できます。

~~~python
from winmltools.utils import save_model
# Save the produced ONNX model in binary format
save_model(model_onnx, 'example.onnx')
# Save the produced ONNX model in text format
from winmltools.utils import save_text
save_text(model_onnx, 'example.txt')
~~~

> [!NOTE]
>Core MLTools が Apple によって提供された Python パッケージが Windows でご利用いただけません。 このパッケージを Windows にインストールする必要がある場合は、リポジトリからパッケージを直接インストールしてください。

```console
pip install git+https://github.com/apple/coremltools
```

## <a name="convert-coreml-models-with-image-inputs-or-outputs"></a>イメージの入力または出力を持つ CoreML モデルに変換します。

ONNX には画像を表す型がないため、Core ML の画像モデル (画像を入力または出力として使うモデル) を変換するには、前処理と後処理の手順が必要になります。

前処理の目的は、入力画像を ONNX のテンソルとして適切な形式にすることです。 たとえば、*X* が [C, H, W] という形状の Core ML の画像入力であるとします。 ONNX では、変数 *X* は同じ形状の浮動小数点テンソルとなり、*X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] に画像の赤/緑/青チャネルが格納されます。 Core ML のグレー スケール画像については、ONNX での形式は [1, H, W] テンソルになります。これはチャネルが 1 つしかないためです。

元の Core ML モデルの出力が画像の場合は、ONNX の出力の浮動小数点テンソルを手動で画像に変換します。 基本的な手順は 2 つあります。 最初の手順として、255 より大きい値を 255 に切り詰め、すべての負の値を 0 に変更します。 2 番目の手順として、すべてのピクセル値を整数に丸めます (0.5 を加えてから小数点以下を切り捨てます)。 出力のチャネルの順序 (RGB、BGR など) は Core ML モデルに示されています。 適切な画像出力を生成するには、転置やシャッフルによって目的の形式を回復する必要がある場合があります。

ここで、ONNX と Core ML の形式の違いを示す実際の変換の例として、[GitHub](https://github.com/likedan/Awesome-CoreML-Models) からダウンロードできる FNS-Candy という Core ML モデルを見てみましょう。 Python 環境で後続のすべてのコマンドが実行されることに注意してください。

まず、Core ML モデルを読み込み、入力形式と出力形式を調べます。

~~~python
from coremltools.models.utils import load_spec
model_coreml = load_spec('FNS-Candy.mlmodel')
model_coreml.description # Print the content of Core ML model description
~~~

画面出力:

~~~console
...
input {
    ...
      imageType {
      width: 720
      height: 720
      colorSpace: BGR
    ...
}
...
output {
    ...
      imageType {
      width: 720
      height: 720
      colorSpace: BGR
    ...
}
...
~~~

この場合、入力と出力はどちらも 720x720 の BGR 画像です。 次の手順では、WinMLTools を使って Core ML モデルを変換します。

~~~python
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_coreml
model_onnx = convert_coreml(model_coreml, 7, name='FNSCandy')    
~~~


ONNX でのモデルの入力形式と出力形式を確認する別の方法として、次のコマンドを使用できます。

~~~python
model_onnx.graph.input # Print out the ONNX input tensor's information
~~~

画面出力:

~~~console
...
  tensor_type {
    elem_type: FLOAT
    shape {
      dim {
        dim_param: "None"
      }
      dim {
        dim_value: 3
      }
      dim {
        dim_value: 720
      }
      dim {
        dim_value: 720
      }
    }
  }
...
~~~

生成された ONNX の入力 (以下 *X*) は 4-D テンソルです。 最後の 3 つの軸はそれぞれ C-、H-、W-軸です。 1 次元目は "None" で、この ONNX モデルが任意の数の画像に適用できることを意味します。 このモデルを適用して 2 つの画像を一括で処理する場合、最初の画像は *X*[0, :, :, :] に対応し、2 番目の画像は *X*[1, :, :, :] に対応します。 最初の画像の青/緑/赤のチャネルは *X*[0, 0, :, :]/*X*[0, 1, :, :]/*X*[0, 2, :, :] となり、2 番目の画像も同様です。

~~~python
model_onnx.graph.output # Print out the ONNX output tensor's information
~~~

画面出力:

~~~console
...
  tensor_type {
    elem_type: FLOAT
    shape {
      dim {
        dim_param: "None"
      }
      dim {
        dim_value: 3
      }
      dim {
        dim_value: 720
      }
      dim {
        dim_value: 720
      }
    }
  }
...
~~~

ご覧のように、生成される形式は元のモデルの入力形式と同じです。 ただし、これは画像ではありません。画像では、ピクセル値が不動小数点数ではなく整数になります。 再び画像に変換するには、255 より大きい値を 255 に切り詰め、負の値を 0 に変更し、すべての少数を整数に丸めます。

## <a name="convert-scikit-learn-models"></a>Scikit-learn モデルに変換します。

次のコード スニペットでは、scikit-learn で線形サポート ベクトル マシンをトレーニングし、モデルを ONNX に変換します。

~~~python
# First, we create a toy data set.
# The training matrix X contains three examples, with two features each.
# The label vector, y, stores the labels of all examples.
X = [[0.5, 1.], [-1., -1.5], [0., -2.]]
y = [1, -1, -1]

# Then, we create a linear classifier and train it.
from sklearn.svm import LinearSVC
linear_svc = LinearSVC()
linear_svc.fit(X, y)

# To convert scikit-learn models, we need to specify the input feature's name and type for our converter. 
# The following line means we have a 2-D float feature vector, and its name is "input" in ONNX.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_sklearn
from winmltools.convert.common.data_types import FloatTensorType
linear_svc_onnx = convert_sklearn(linear_svc, 7, name='LinearSVC',
                                  initial_types=[('input', FloatTensorType([1, 2]))])    

# Now, we save the ONNX model into binary format.
from winmltools.utils import save_model
save_model(linear_svc_onnx, 'linear_svc.onnx')

# If you'd like to load an ONNX binary file, our tool can also help.
from winmltools.utils import load_model
linear_svc_onnx = load_model('linear_svc.onnx')

# To see the produced ONNX model, we can print its contents or save it in text format.
print(linear_svc_onnx)
from winmltools.utils import save_text
save_text(linear_svc_onnx, 'linear_svc.txt')

# The conversion of linear regression is very similar. See the example below.
from sklearn.svm import LinearSVR
linear_svr = LinearSVR()
linear_svr.fit(X, y)
linear_svr_onnx = convert_sklearn(linear_svr, 7, name='LinearSVR', 
                                  initial_types=[('input', FloatTensorType([1, 2]))])   
~~~

前に、と convert_sklearn は最初の引数と 2 番目の引数の target_opset scikit-learn モデルを受け取ります。 ユーザーは、`LinearSVC` を `RandomForestClassifier` などの他の scikit-learn モデルに置き換えることができます。 注意してください[mlgen](mlgen.md)を使用して、`name`クラス名と変数を生成するパラメーター。 `name` が指定されていない場合は GUID が生成されますが、これは C++/C# などの言語の名前付け規則に準拠しません。

## <a name="convert-scikit-learn-pipelines"></a>Scikit-learn のパイプラインを変換します。

次に、scikit-learn パイプラインを ONNX に変換する方法を示します。

~~~python
# First, we create a toy data set.
# Notice that the first example's last feature value, 300, is large.
X = [[0.5, 1., 300.], [-1., -1.5, -4.], [0., -2., -1.]]
y = [1, -1, -1]

# Then, we declare a linear classifier.
from sklearn.svm import LinearSVC
linear_svc = LinearSVC()

# One common trick to improve a linear model's performance is to normalize the input data.
from sklearn.preprocessing import Normalizer
normalizer = Normalizer()

# Here, we compose our scikit-learn pipeline. 
# First, we apply our normalization. 
# Then we feed the normalized data into the linear model.
from sklearn.pipeline import make_pipeline
pipeline = make_pipeline(normalizer, linear_svc)
pipeline.fit(X, y)

# Now, we convert the scikit-learn pipeline into ONNX format. 
# Compared to the previous example, notice that the specified feature dimension becomes 3.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_sklearn
from winmltools.convert.common.data_types import FloatTensorType, Int64TensorType
pipeline_onnx = convert_sklearn(linear_svc, name='NormalizerLinearSVC',
                                input_features=[('input', FloatTensorType([1, 3]))])   

# We can print the fresh ONNX model.
print(pipeline_onnx)

# We can also save the ONNX model into binary file for later use.
from winmltools.utils import save_model
save_model(pipeline_onnx, 'pipeline.onnx')

# Our conversion framework provides limited support of heterogeneous feature values.
# We cannot have numerical types and string type in one feature vector. 
# Let's assume that the first two features are floats and the last feature is integer (encoded a categorical attribute).
X_heter = [[0.5, 1., 300], [-1., -1.5, 400], [0., -2., 100]]

# One popular way to represent categorical is one-hot encoding.
from sklearn.preprocessing import OneHotEncoder
one_hot_encoder = OneHotEncoder(categorical_features=[2])

# Let's initialize a classifier. 
# It will be right after the one-hot encoder in our pipeline.
linear_svc = LinearSVC()

# Then, we form a two-stage pipeline.
another_pipeline = make_pipeline(one_hot_encoder, linear_svc)
another_pipeline.fit(X_heter, y)

# Now, we convert, save, and load the converted model. 
# For heterogeneous feature vectors, we need to seperately specify their types for all homogeneous segments.
# The automatic code generator (mlgen) uses the name parameter to generate class names.
another_pipeline_onnx = convert_sklearn(another_pipeline, name='OneHotLinearSVC',
                                        input_features=[('input', FloatTensorType([1, 2])),
                                        ('another_input', Int64TensorType([1, 1]))])
save_model(another_pipeline_onnx, 'another_pipeline.onnx')
from winmltools.utils import load_model
loaded_onnx_model = load_model('another_pipeline.onnx')

# Of course, we can print the ONNX model to see if anything went wrong.
print(another_pipeline_onnx)
~~~

## <a name="convert-tensorflow-models"></a>Tensorflow モデルを変換します。

次のコードは、固定された tensorflow モデルからモデルを変換する方法の例です。 Tensorflow モデルの使用可能な出力名を取得するには、使用することができます[summarize_graph ツール](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/graph_transforms)

~~~python
import winmltools
import tensorflow

filename = 'frozen-model.pb'
output_names = ['output:0']

graph_def = graph_pb2.GraphDef()
with open(filename, 'rb') as file:
  graph_def.ParseFromString(file.read())
g = tf.import_graph_def(graph_def, name='')

with tf.Session(graph=g) as sess:
  converted_model = winmltools.convert_tensorflow(sess.graph, 7, output_names=['output:0'])
  winmltools.save_model(converted_model)
~~~

WinMLTools コンバーターの使用で tf2onnx.tfonnx.process_tf_graph [TF2ONNX](https://github.com/onnx/tensorflow-onnx)します。 

## <a name="convert-to-floating-point-16"></a>浮動小数点 16 への変換します。

WinMLTools には、浮動小数点浮動に 32 ポイントのサイズを半分に減らすことで、モデルを効果的に圧縮、16 の表現で表されるモデルの変換がサポートしています。 

> [!NOTE]
> 量子化すると、結果として得られるモデルの精度が失われる可能性があります。 アプリケーションに展開する前に、モデルの精度を確認することを確認します。

次には、ONNX のバイナリ ファイルから直接変換する場合、完全な例を示します。 

~~~python
from winmltools.utils import convert_float_to_float16
from winmltools.utils import load_model, save_model
onnx_model = load_model('model.onnx')
new_onnx_model = convert_float_to_float16(onnx_model)
save_model(new_onnx_model, 'model_fp16.onnx')
~~~

パラメーター: per_channel:場合は、量子化を True に設定するは、[n、h、w] の形式で Conv 演算子の初期化 tensors 内の各チャンネルの dequantize 直線的には。 既定では、これは True に設定しています。

`help(winmltools.utils.convert_float_to_float16)`、このツールの詳細を見つけることができます。 浮動小数点データ 16 WinMLTools で現在のみに準拠して[IEEE 754 浮動ポイント標準 (2008)](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)します。

>[!NOTE]
>モデルのサイズを小さくすると、精度が失われる可能性があります。 常に、アプリケーションを展開する前に、結果として得られるモデルの精度を確認することをお勧めします。

## <a name="quantize-onnx-model"></a>ONNX モデルを量子化します。

WinMLTools では、quantize 演算子を使用して既存の ONNX モデルを圧縮もサポートしています。 このツールでは、32 ビットの 8 ビット データに浮動小数点データから線形の量子化がサポートされています。 

> [!NOTE]
>量子化すると、結果として得られるモデルの精度が失われる可能性があります。 アプリケーションに展開する前に、モデルの精度を確認することを確認します。

次には、ONNX のバイナリ ファイルから直接変換する場合、完全な例を示します。 
~~~python
import winmltools

model = winmltools.load_model('model.onnx')
quantized_model = winmltools.quantize(model, per_channel=True, nbits=8, use_dequantize_linear=True)
winmltools.save_model(quantized_model, 'quantized.onnx')

~~~
入力パラメーターの定義:

- `per_channel`:場合は、量子化を True に設定するは、[n、h、w] の形式で初期化された各 tensors 内の各チャンネルの dequantize は直線的にします。 既定では、このパラメーターが True に設定されます。
- `nbits`: 量子化された値を表すビット数。 現在 8 ビットのみがサポートされています。 
- `use_dequantize_linear`:場合は、量子化を True に設定するは、[n、h、w] の形式で Conv 演算子の初期化 tensors 内の各チャンネルの dequantize 直線的には。 既定では、これは True に設定しています。


## <a name="create-custom-onnx-operators"></a>カスタムの ONNX オペレーターを作成します。

カスタムを埋め込むにはカスタム演算子関数を記述することができます、Keras の Core ML モデルに変換するときに[演算子](https://github.com/onnx/onnx/blob/master/docs/Operators.md)ONNX グラフにします。 変換中は、コンバーターが、Keras レイヤーまたは ONNX オペレーターに Core ML LayerParameter を変換する関数を呼び出すし、演算子のノード全体のグラフに接続します。

1. ONNX サブグラフの構築用のカスタム関数を作成します。
2. 呼び出す`winmltools.convert_keras`または`winmltools.convert_coreml`カスタム関数をカスタム レイヤー名のマップを使用します。S
3. 該当する場合は、推論ランタイムのカスタムのレイヤーを実装します。  

次の例では、Keras のしくみを説明します。

~~~python
# Define the activation layer.
class ParametricSoftplus(keras.layers.Layer):
    def __init__(self, alpha, beta, **kwargs):
    ...
    ...
    ...

# Create the convert function.
def convert_userPSoftplusLayer(scope, operator, container):
      return container.add_node('ParametricSoftplus', operator.input_full_names, operator.output_full_names,
        op_version=1, alpha=operator.original_operator.alpha, beta=operator.original_operator.beta)

winmltools.convert_keras(keras_model, 7,
    custom_conversion_functions={ParametricSoftplus: convert_userPSoftplusLayer })
~~~

[!INCLUDE [help](includes/get-help.md)]
