---
title: モデルの入力を評価する
description: モデルの入力に対して評価を実行し、予測を取得する方法について説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 9f23b272f85f1bd3beb60bfea341c522941fa854
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156720"
---
# <a name="evaluate-the-model-inputs"></a>モデルの入力を評価する

モデルの入力と出力に値をバインドすると、モデルの入力を評価し、その予測を取得する準備が整います。

モデルを実行するには、 [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession)で**Evaluate*** メソッドを呼び出します。 [LearningModelEvaluationResult](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult)を使用して、出力機能を確認できます。

## <a name="example"></a>例

次の例では、セッションに対して評価を実行し、バインドと一意の相関 ID を渡します。 次に、確率の一覧として出力を解析し、モデルが認識できるさまざまな要素のラベルの一覧と照合して、結果をコンソールに書き込みます。

```cs
// How many times an evaluation has been run
private int runCount = 0;

private void EvaluateModel(
    LearningModelSession session,
    LearningModelBinding binding,
    string outputName,
    List<string> labels)
{
    // Process the frame with the model
    var results =
        await session.EvaluateAsync(binding, $"Run {++runCount}");

    // Retrieve the results of evaluation
    var resultTensor = results.Outputs[outputName] as TensorFloat;
    var resultVector = resultTensor.GetAsVectorView();

    // Find the top 3 probabilities
    List<(int index, float probability)> indexedResults = new List<(int, float)>();

    for (int i = 0; i < resultVector.Count; i++)
    {
        indexedResults.Add((index: i, probability: resultVector.ElementAt(i)));
    }

    // Sort the results in order of highest probability
    indexedResults.Sort((a, b) =>
    {
        if (a.probability < b.probability)
        {
            return 1;
        }
        else if (a.probability > b.probability)
        {
            return -1;
        }
        else
        {
            return 0;
        }
    });

    // Display the results
    for (int i = 0; i < 3; i++)
    {
        Debug.WriteLine(
            $"\"{labels[indexedResults[i].index]}\" with confidence of {indexedResults[i].probability}");
    }
}
```

## <a name="device-removal"></a>デバイスの削除

デバイスが使用できなくなった場合、または別のデバイスを使用する場合は、セッションを閉じて新しいセッションを作成する必要があります。

場合によっては、 [DirectX のドキュメント](https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios)で説明されているように、グラフィックスデバイスのアンロードと再読み込みが必要になることがあります。

Windows ML を使用する場合は、このケースを検出してセッションを閉じる必要があります。 デバイスの削除または再初期化から回復するには、新しいセッションを作成します。これにより、デバイス選択ロジックが再度実行されるようになります。

このエラーが発生する最も一般的なケースは、 [LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate)の実行中です。 デバイスの削除またはリセットの場合、 [LearningModelEvaluationResult](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult.errorstatus)は[DXGI_ERROR_DEVICE_REMOVED](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error)または[DXGI_ERROR_DEVICE_RESET](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error)になります。

## <a name="see-also"></a>関連項目

* 先の：[モデルを作成する](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
