---
title: モデルの入力を評価する
description: 予測を取得するためにモデルの入力に関する評価を実行する方法について説明します。
ms.date: 4/1/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning
ms.localizationpriority: medium
ms.openlocfilehash: 9f23b272f85f1bd3beb60bfea341c522941fa854
ms.sourcegitcommit: 2139506ff12b7205283288c4bbac866ddfa812f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "70156720"
---
# <a name="evaluate-the-model-inputs"></a>モデルの入力を評価する

モデルの入力と出力に値をバインドすると、モデルの入力を評価し、その予測を取得する準備が整います。

モデルを実行するには、[LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession) でいずれかの **Evaluate*** メソッドを呼び出します。 [LearningModelEvaluationResult](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult) を使用して、出力機能を調べることができます。

## <a name="example"></a>例

次の例では、セッションで評価を実行し、バインドと一意の関連付け ID を渡します。 次に、出力を確率の一覧として解析し、それをモデルが認識可能なさまざまなものに関するラベルの一覧と照合して、結果をコンソールに書き込みます。

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

デバイスが使用できなくなった場合や、別のデバイスを使用したい場合は、セッションを閉じて新しいセッションを作成する必要があります。

場合によっては、[DirectX のドキュメント](https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios)で説明されているように、グラフィックス デバイスのアンロードと再読み込みが必要になることがあります。

Windows ML を使用している場合は、このケースを検出してセッションを閉じる必要があります。 デバイスの削除または再初期化から回復するには、新しいセッションを作成します。これにより、デバイス選択ロジックがトリガーされて再度実行されます。

このエラーは一般的に、[LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate) の実行中の場合に最も表示されます。 デバイスの削除またはリセットが発生した場合、[LearningModelEvaluationResult.ErrorStatus](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult.errorstatus) は [DXGI_ERROR_DEVICE_REMOVED](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error) または [DXGI_ERROR_DEVICE_RESET](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error) になります。

## <a name="see-also"></a>関連項目

* 前の手順: [モデルを作成する](bind-a-model.md)

[!INCLUDE [help](../includes/get-help.md)]
