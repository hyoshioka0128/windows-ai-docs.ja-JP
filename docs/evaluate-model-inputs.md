---
author: eliotcowley
title: モデルの入力を評価します。
description: 予測を取得するモデルの入力の評価を実行する方法について説明します。
ms.author: elcowle
ms.date: 2/19/2019
ms.topic: article
keywords: windows 10、windows の ai、windows の ml、winml、windows の機械学習
ms.localizationpriority: medium
ms.openlocfilehash: 8fd2e3333383e53bb8d06fb2d1e63f79a6bd78de
ms.sourcegitcommit: 5e212634a0617fc003bae2bf477feab3169e28f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59474949"
---
# <a name="evaluate-the-model-inputs"></a>モデルの入力を評価します。

モデルの入力と出力への値をバインドした後、モデルの入力を評価し、その予測を取得する準備が整いました。

呼び出しのいずれかのモデルを実行する、 **Evaluate*** メソッドを[LearningModelSession](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession)します。 使用することができます、 [LearningModelEvaluationResult](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult)出力機能を確認します。

## <a name="example"></a>例

次の例で、セッションで、バインドと一意の関連付け ID を渡して、評価版を実行します 出力を解析しました、確率の一覧と、モデルが、認識し、結果をコンソールに書き込むには、さまざまなモ ノのラベルの一覧に一致。

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

デバイスが利用できなくなった場合に、別のデバイスを使用したい場合や、セッションを終了して、新しいセッションを作成する必要があります。

場合によっては、グラフィックス デバイス必要がありますをアンロードして再読み込みするで説明したように、 [DirectX のドキュメント](https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios)します。

Windows の ML を使用する場合は、このケースを検出し、セッションを閉じる必要があります。 デバイスの削除または再初期化から回復するには、もう一度実行するデバイスの選択ロジックをトリガーする、新しいセッションを作成します。

このエラーを表示、最も一般的なケースは、中に[LearningModelSession.Evaluate](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelsession.evaluate)します。 場合はデバイスを削除するか、リセット[LearningModelEvaluationResult.ErrorStatus](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.learningmodelevaluationresult.errorstatus)なります[DXGI_ERROR_DEVICE_REMOVED](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error)または[DXGI_ERROR_DEVICE_RESET](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-error)します。

## <a name="see-also"></a>関連項目

* 先の：[モデルをバインドします。](bind-a-model.md)

[!INCLUDE [help](includes/get-help.md)]
