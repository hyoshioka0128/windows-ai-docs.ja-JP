---
author: wschin
title: ML モデルを WinMLTools で ONNX に変換します。
description: WinMLTools を使用して ML モデルを ONNX 形式に変換する方法について説明します。
ms.author: wechi
ms.date: 4/18/2019
ms.topic: article
keywords: windows 10、windows の machine learning、WinML、WinMLTools、ONNX、ONNXMLTools、scikit、学習、Core ML、Keras
ms.localizationpriority: medium
ms.openlocfilehash: 76d3436cf52a8e658881e7b8cbdd437a53a00bb1
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66180864"
---
# <a name="convert-ml-models-to-onnx-with-winmltools"></a>ML モデルを WinMLTools で ONNX に変換します。

[WinMLTools](https://pypi.org/project/winmltools/) ONNX にさまざまなトレーニング フレームワークで作成された機械学習モデルを変換することができます。 拡張機能は[ONNXMLTools](https://github.com/onnx/onnxmltools)と[TF2ONNX](https://github.com/onnx/tensorflow-onnx) Windows ML で使用するために ONNX モデルを変換します。

現在、WinMLTools には、次のフレームワークからの変換がサポートされています。

- Apple の Core ML
- Keras
- scikit、について説明します
- lightgbm
- xgboost
- libSVM
- TensorFlow (試験段階)

その他の ML フレームワークからエクスポートする方法についてを参照してください、 [ONNX チュートリアル](https://github.com/onnx/tutorials)GitHub でします。

この記事に WinMLTools を使用する方法について説明します。

- ONNX Core ML モデルに変換します。
- 変換 scikit-に ONNX モデルを説明します。
- TensorFlow モデルを ONNX に変換します。
- 適用後のトレーニング ONNX モデルに量子化の重み
- 16 ビットの浮動小数点モデル精度のモデルをポイントする浮動小数点を変換します。
- カスタムの ONNX オペレーターを作成します。

>[!NOTE]
>[WinMLTools の最新バージョン](https://pypi.org/project/winmltools/1.3.0/)ONNX opsets 7 と 8 でそれぞれ指定された ONNX バージョン 1.2.2 および 1.3 への変換をサポートしています。 ツールの以前のバージョンでは、ONNX 1.3 のサポートはありません。

## <a name="install-winmltools"></a>WinMLTools のインストール

WinMLTools は Python パッケージ (**winmltools**) Python バージョン 2.7 および 3.6 をサポートします。 データ サイエンス プロジェクトを扱う場合は、Anaconda などのサイエンス向けの Python ディストリビューションをインストールすることをお勧めします。

> [!NOTE]
> WinMLTools は、Python 3.7 を現在サポートしていません。

WinMLTools に依存して、[標準的な Python パッケージのインストール処理](https://packaging.python.org/installing/)します。 Python 環境から次のコマンドを実行します。

```console
pip install winmltools
```

WinMLTools には次の依存関係があります。

- **numpy** v1.10.0 +
- **protobuf** v.3.6.0+
- **onnx** v1.3.0 +
- **onnxmltools** v1.3.0 +
- **tf2onnx** v0.3.2+

依存パッケージを更新するには、実行、`pip`コマンドと、`-U`引数。

```console
pip install -U winmltools
```

さまざまなコンバーターは、さまざまなパッケージをインストールする必要があります。

**Libsvm**、ダウンロードできる**libsvm ホイール**web のさまざまなソースからです。 1 つの例をご覧、[カリフォルニア大学アーバイン校の web サイト](https://www.lfd.uci.edu/~gohlke/pythonlibs/#libsvm)します。

**Coremltools**、現在 Apple が Windows 上の Core ML パッケージを配布できません。 ソースからインストールすることができます。

```console
pip install git+https://github.com/apple/coremltools
```

次の[onnxmltools](https://github.com/onnx/onnxmltools)について詳しくは、GitHub の**onnxmltools**依存関係。

パッケージ固有のドキュメントで WinMLTools を使用する方法の詳細を確認できます、`help`関数。

```console
help(winmltools)
```

## <a name="convert-core-ml-models"></a>コア ML モデルを変換します。

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
> Convert_coreml() への呼び出しでは、2 番目のパラメーターは、target_opset と既定の名前空間の演算子のバージョン番号を参照して`ai.onnx`します。 これらの演算子の詳細を参照してください[ここ](https://github.com/onnx/onnx/blob/master/docs/Operators.md)します。 このパラメーターは WinMLTools、(バージョン 1.2.2 および 1.3 がサポートされている現在) 別の ONNX バージョンを対象とする開発者の最新バージョンで利用できます。 Windows で実行するモデルに変換する 10 年 2018年 10 月の更新を使用`target_opset`7 (ONNX v1.2.2)。 使用したモデルを WinML が受け入れるの Windows 10 ビルド 17763 より大きい、 `target_opset` 7 および 8 (ONNX v.1.3)。 [リリース ノート](release-notes.md)セクションには、さまざまなビルドでサポートされている WinML min と max ONNX バージョンも含まれています。

`model_onnx` ONNX [ModelProto](https://github.com/onnx/onnxmltools/blob/0f453c3f375c1ae928b83a4c7909c82c013a5bff/onnxmltools/proto/onnx-ml.proto#L176)オブジェクト。 これは 2 つの異なる形式で保存できます。

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

## <a name="convert-core-ml-models-with-image-inputs-or-outputs"></a>イメージの入力または出力の Core ML モデルを変換します。

ONNX でイメージの種類の不足、Core ML イメージ モデル (入力または出力としてイメージを使用してモデル) に変換するいくつかの処理前および処理後の手順が必要です。

前処理の目的は、入力画像を ONNX のテンソルとして適切な形式にすることです。 たとえば、*X* が [C, H, W] という形状の Core ML の画像入力であるとします。 ONNX では、変数 *X* は同じ形状の浮動小数点テンソルとなり、*X*[0, :, :]/*X*[1, :, :]/*X*[2, :, :] に画像の赤/緑/青チャネルが格納されます。 コア ML でのイメージをグレースケールでは、その形式には [1, H、W]-tensors ONNX でチャネルを 1 つのみがあるので。

元の Core ML モデルの出力が画像の場合は、ONNX の出力の浮動小数点テンソルを手動で画像に変換します。 基本的な手順は 2 つあります。 最初の手順として、255 より大きい値を 255 に切り詰め、すべての負の値を 0 に変更します。 2 番目の手順として、すべてのピクセル値を整数に丸めます (0.5 を加えてから小数点以下を切り捨てます)。 コア ML モデルでは、(たとえば、RGB または BGR) 出力チャネルの順序が示されます。 適切な画像出力を生成するには、転置やシャッフルによって目的の形式を回復する必要がある場合があります。

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

この場合、入力と出力の両方は 720 x 720 BGR-イメージです。 次の手順では、WinMLTools を使って Core ML モデルを変換します。

~~~python
# The automatic code generator (mlgen) uses the name parameter to generate class names.
from winmltools import convert_coreml
model_onnx = convert_coreml(model_coreml, 7, name='FNSCandy')
~~~

モデルの入力を表示し、出力に ONNX 形式に別の方法では、次のコマンドを使用します。

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

## <a name="convert-scikit-learn-models"></a>変換 scikit-モデルを説明します。

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

以前と同様`convert_sklearn`、scikit を受け取る-最初の引数としてのモデルについて説明しますと、`target_opset`の 2 番目の引数。 ユーザーは、`LinearSVC` を `RandomForestClassifier` などの他の scikit-learn モデルに置き換えることができます。 注意してください[mlgen](mlgen.md)を使用して、`name`クラス名と変数を生成するパラメーター。 `name` が指定されていない場合は GUID が生成されますが、これは C++/C# などの言語の名前付け規則に準拠しません。

## <a name="convert-scikit-learn-pipelines"></a>Scikit の変換のパイプラインについて説明します

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

# We can also save the ONNX model into a binary file for later use.
from winmltools.utils import save_model
save_model(pipeline_onnx, 'pipeline.onnx')

# Our conversion framework provides limited support of heterogeneous feature values.
# We cannot have numerical types and string types in one feature vector.
# Let's assume that the first two features are floats and the last feature is integers (encoded a categorical attribute).
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
# For heterogeneous feature vectors, we need to separately specify their types for
# all homogeneous segments.
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

## <a name="convert-tensorflow-models"></a>TensorFlow モデルを変換します。

次のコードは、固定された TensorFlow モデルからモデルを変換する方法の例です。 TensorFlow モデルの名前の出力を使用可能なを取得するために、使用することができます、 [summarize_graph ツール](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/graph_transforms)します。

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

WinMLTools コンバーターを使用して`tf2onnx.tfonnx.process_tf_graph`で[TF2ONNX](https://github.com/onnx/tensorflow-onnx)します。

## <a name="convert-to-floating-point-16"></a>浮動小数点 16 への変換します。

WinMLTools 浮動小数点浮動に 32 ポイント 16 の表現で表されるモデルの変換をサポートしています (IEEE 754 半分)、実質的に半分のサイズを減らすことで、モデルを圧縮します。

> [!NOTE]
> 16 の浮動小数点モデルに変換すると、精度が失われる可能性があります。 アプリケーションに展開する前に、モデルの精度を確認することを確認します。

次には、ONNX のバイナリ ファイルから直接変換する場合、完全な例を示します。

~~~python
from winmltools.utils import convert_float_to_float16
from winmltools.utils import load_model, save_model
onnx_model = load_model('model.onnx')
new_onnx_model = convert_float_to_float16(onnx_model)
save_model(new_onnx_model, 'model_fp16.onnx')
~~~

`help(winmltools.utils.convert_float_to_float16)`、このツールの詳細を見つけることができます。 浮動小数点 16 WinMLTools で現在のみに準拠して[IEEE 754 浮動ポイント標準 (2008)](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)します。

## <a name="post-training-weight-quantization"></a>トレーニング後の重みの量子化

WinMLTools には、8 ビット整数表現に浮動小数点 32 で表されるモデルの圧縮もサポートしています。 モデルに応じて最大 75% のディスク フット プリントの削減これが生成されます。 この短縮は、後のトレーニングと呼ばれる手法によって行われます。 加重量子化、場所、モデルが分析され、ストアド tensor 重みは、32 ビット浮動小数点データから 8 ビットのデータに削減されます。

> [!NOTE]
> 量子化の重みのトレーニング後、結果として得られるモデルの精度が失われる可能性があります。 アプリケーションに展開する前に、モデルの精度を確認することを確認します。

ONNX のバイナリ ファイルから直接変換する方法を示す完全な例を次に示します。

```python
import winmltools

model = winmltools.load_model('model.onnx')
packed_model = winmltools.quantize(model, per_channel=True, nbits=8, use_dequantize_linear=True)
winmltools.save_model(packed_model, 'quantized.onnx')
```

ここではいくつかの情報への入力パラメーターについて`quantize`:

- `per_channel` :場合に設定`True`、この直線的に [n、h、w] の形式で初期化された各 tensor の各チャネルの量子化されます。 既定では、このパラメーターに設定`True`します。
- `nbits` :量子化された値を表すビット数。 現在 8 ビットのみがサポートされています。
- `use_dequantize_linear` :場合設定`True`、Conv 演算子 [n、h、w] の形式で初期化された tensors 内の各チャンネルを dequantize これは直線的にします。 既定では、この設定は`True`します。

## <a name="create-custom-onnx-operators"></a>カスタムの ONNX オペレーターを作成します。

カスタムを埋め込むにはカスタム演算子関数を記述することができます、Keras の Core ML モデルに変換するときに[演算子](https://github.com/onnx/onnx/blob/master/docs/Operators.md)ONNX グラフにします。 変換中は、コンバーターが、Keras レイヤーまたは ONNX オペレーターに Core ML LayerParameter を変換する関数を呼び出すし、演算子のノード全体のグラフに接続します。

1. ONNX サブグラフの構築用のカスタム関数を作成します。
2. 呼び出す`winmltools.convert_keras`または`winmltools.convert_coreml`カスタム関数をカスタム レイヤー名のマップを使用します。
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

[!INCLUDE [help](../includes/get-help.md)]
