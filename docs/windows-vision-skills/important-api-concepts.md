---
author: eliotcowley
title: 重要な API の概念
description: Windows のビジョン スキル API の重要な概念について説明します。
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: windows 10、windows の ai windows vision スキル
ms.localizationpriority: medium
ms.openlocfilehash: f34b3916c713892e3bd2bbd2f7cd1e7483df6ddb
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179944"
---
# <a name="important-api-concepts"></a>重要な API の概念

> [!NOTE]
> いくつかの情報は、リリース版の発売までに著しく変更される可能性がありますが、リリース前の製品に関連します。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

[Microsoft.AI.Skills.SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview)名前空間が一連の Windows でスキルの実装についてのすべてのスキルだけでなくクラスとヘルパー メソッドによって拡張する基本インターフェイスを提供します。

この API は、方法スキルの作業を効率化し、開発者がそれらと対話する方法に過ぎません。 目標は、各スキルのロジックの API specificities で抽象化し、ソリューションとアプリケーションの広範なセットを代わりに一貫性のある開発者向けの直感を活用することです。 OS Api との相互運用を容易にする Windows プリミティブを利用するものではも。 これは、すべてのスキルの間で、開発者のフローと API の相互作用を標準化するテンプレートから派生するを構成します。

そのため、少なくとも次のインターフェイスを実装するすべてのスキルが期待される結果します。

<br/>

| 名前 | 説明 |
|------|-------------|
| [ISkillDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) | スキルについて説明し、その要件 (入力、出力、バージョンなど) を公開します。 ファクトリとして機能、 [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill)します。 |
| [ISkillBinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding) | インデックス付きのコンテナーとして機能[ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)します。 前後に渡される変数の入力と出力のコンジットとして機能すること、 [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill)します。 前処理と後処理の入力/出力データを処理しへのアクセスを簡略化します。 |
| [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill) | その入力の処理とを経由してその出力を形成のコア ロジックを公開、 [ISkillBinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding)します。 ファクトリとして機能、 [ISkillBinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding)します。 |

スキルは最適に機能を利用して、ハードウェア (CPU、GPU など) の各システム上で実行するものです。 これらのハードウェア アクセラレーション デバイスが派生することによって表される、 [ISkillExecutionDevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice)インターフェイスに関連付けられている、 [SkillExecutionDeviceKind](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicekind)します。 そのため、 [ISkillDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor)派生クラスは、検索、フィルター、およびのセットを公開する必要がある[ISkillExecutionDevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice)オブジェクトが現在実行できるホスト システムで使用できる、 [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill)ロジック。

これによって、最適なスキルのパッケージを使う開発者がユーザーのシステム上で実行時のサポートされているハードウェア リソースを利用する方法を選択します。 いくつかあります[ISkillExecutionDevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice)派生クラスで利用可能と定義済みの利便性の既に ([SkillExecutionDeviceCPU](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicecpu)と[SkillExecutionDeviceDirectX](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicedirectx)).

スキル、正しい形式で入力と出力の変数が渡されることを確認するには、 [ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)インターフェイスを定義します。 定義済みの形式の値をカプセル化するものです。 この値は、の派生クラスで表される[ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue)、既に定義されていると利便性のために使用できる複数の一般的な派生を持つ ([ISkillFeatureTensorValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensorvalue)、 [SkillFeatureImageValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeatureimagevalue)、および[SkillFeatureMapValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeaturemapvalue))。

各[ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue)派生物が、対応する[ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor)スキルでサポートされている予期された形式を記述する定義の導関数 ([ISkillFeatureTensorDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensordescriptor)、 [ISkillFeatureImageDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeatureimagedescriptor)、および[ISkillFeatureMapDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturemapdescriptor))。 これら[ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor)派生クラスは、ファクトリ オブジェクトとしても機能、 [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue)オブジェクトについて説明します。

プリミティブを使用して割り当てる場合、インスタンス化時に[ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue)によって提供される説明と一致しません、 [ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor)認識されて、特定の自動変換それぞれの種類には、シームレスに (必要に応じて、1 つまたは縦横比が異なる場合のトリミングとは異なる形式でイメージをバインドするときにトランス コードなど) の発生します。

## API のフロー <a name="APIFlow"></a>

派生させる基底インターフェイスからの同じセットのすべてのスキル[Microsoft.AI.Skills.SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview)、通常は、次の操作にまとめることがこれと同じフローに従い、これらはすべて。

<div style="text-align:center" markdown="1">

![Windows のビジョンのスキルを取り込み、アプリケーションからの API 呼び出しの通常のシーケンスを示す Windows Vision スキル API フロー図](../images/vision-skills-flow.png)

</div>

1) インスタンスを作成、 [ISkillDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor)から派生します。

2) 手順 1 からインスタンスを使用して利用可能な実行デバイスをクエリする (を使用して[ISkillDescriptor.GetSupportedExecutionDevicesAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.getsupportedexecutiondevicesasync)) またはスキップし、直接手順 3. を試行します。

3) 手順 1 のインスタンスと手順 2. の実行が必要なデバイスを使用してスキルをインスタンス化 (を使用して[ISkillDescriptor.CreateSkillAsync(ISkillExecutionDevice)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync)) または (を使用して、スキルの開発者によって決定のいずれかの既定値[ISkillDescriptor.CreateAsync()](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync))。

4) 手順 3 からスキルのインスタンスを使用して、スキル バインディング オブジェクトをインスタンス化 (を使用して[ISkill.CreateSkillBindingAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.createskillbindingasync))。

5) 取得、プリミティブ ([VideoFrame](https://docs.microsoft.com/uwp/api/windows.media.videoframe)、 [IVectorView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.ivectorview_t_)、 [IMapView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.imapview_k_v_)など) からバインド、アプリケーション オブジェクトのバインドに手順 4 (にアクセスして、対応する[ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)名前を使用してインデックスを作成し、呼び出し元[ISkillFeature.SetFeatureValueAsync(Object)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.setfeaturevalueasync))。

6) バインド オブジェクト上で、スキルを実行 (呼び出して[ISkill.EvaluateAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.evaluateasync))。

7) 手順 4 でインスタンス化される、バインド オブジェクトから、出力のプリミティブを取得 (対応にアクセスして[ISkillFeature](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)の名前と、get アクセス操作子の呼び出しを使用してインデックス付き[ISkillFeature.FeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.featurevalue)).

8) 受け取ってし、同じバインディング オブジェクトと新しいプリミティブを使用して 5 の手順を繰り返します。

アクションの表示は、取り込みのためのチュートリアルを参照してください、[アプリから Windows ビジョン スキル](tutorial1.md)します。

[!INCLUDE [help](../includes/get-help-vision.md)]
