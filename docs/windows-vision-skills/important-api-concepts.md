---
title: API の重要な概念
description: Windows ビジョンスキル API の重要な概念について説明します。
ms.date: 4/25/2019
ms.topic: article
keywords: windows 10、windows ai、windows ビジョンのスキル
ms.localizationpriority: medium
ms.openlocfilehash: af73ceb559129bdb78477b41caa4d3741f78d5f7
ms.sourcegitcommit: 577942041c1ff4da60d22af96543c11f5d5fe401
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70156296"
---
# <a name="important-api-concepts"></a>API の重要な概念

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 Microsoft は、ここで提供される情報に関して、明示または黙示を問わず、いかなる保証も行いません。

[SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview)名前空間は、Windows 上のスキルを実装するためのクラスとヘルパーメソッドだけでなく、すべてのスキルによって拡張される基本インターフェイスのセットを提供します。

この API は、スキルのしくみと開発者との対話方法を合理化することを目的としています。 目標は、各スキルのロジックに固有の API を抽象化し、より多くのソリューションやアプリケーションに対して一貫性のある開発者直感を利用できるようにすることです。 また、OS Api との相互運用を容易にする Windows プリミティブを利用することもできます。 これは、すべてのスキルで開発者のフローと API の相互作用を標準化する、から派生するテンプレートを構成します。

そのため、すべてのスキルは、少なくとも次のインターフェイスに実装することを想定しています。

<br/>

| 名前 | 説明 |
|------|-------------|
| [Isの記述子](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor) | スキルに関する情報を提供し、その要件 (入力、出力、バージョンなど) を公開します。 [Iskill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill)のファクトリとして機能します。 |
| [Isのバインド](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding) | [Isの機能](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)のインデックス付きコンテナーとして機能します。 これは、入力および出力変数を[Iskill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill)に渡すためのパイプとして機能します。 入力/出力データのプリプロセスと後処理を処理し、アクセスを簡略化します。 |
| [ISkill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill) | 入力を処理し、 [Isて binding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding)を使用して出力を形成するコアロジックを公開します。 [Iskillbinding](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillbinding)のファクトリとして機能します。 |

スキルは、実行されている各システムのハードウェア機能 (CPU、GPU など) を最適に活用することを目的としています。 これらのハードウェアアクセラレーションデバイスは、[スキル Executiondevicekind](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicekind)に関連付けられている[isare executiondevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice)インターフェイスを派生させることによって表されます。 したがって、 [Isキル](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill)[記述子](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor)の派生は、iskill logic を実行できるホストシステム上で現在使用可能な[iskill executiondevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice)オブジェクトのセットを検索、フィルター処理、および公開する必要があります。

これにより、スキルパッケージを使用する開発者は、ユーザーのシステムで実行時にサポートされているハードウェアリソースをタップする方法を最適に選択できます。 いくつかの[isて executiondevice](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillexecutiondevice)派生クラスが既に定義されており、便利な ([スキル Executiondevicecpu](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicecpu)および[スキル executiondevicedirectx](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillexecutiondevicedirectx)) ために使用できます。

入力変数と出力変数が正しい形式でスキルに渡されるようにするために、 [Isの特徴](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)インターフェイスが定義されています。 これは、定義済みの形式で値をカプセル化することを意図しています。 この値は [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) の派生物によって表されます。これには、複数の共通の派生物が既に定義されており、便利なものがあります ([ISkillFeatureTensorValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensorvalue)、[SkillFeatureImageValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeatureimagevalue)、[SkillFeatureMapValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.skillfeaturemapvalue))。

各 [ISkillFeatureValue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue) 派生には、スキルでサポートされる必要な形式を記述する、対応する [ISkillFeatureDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor) が定義されています ([ISkillFeatureTensorDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturetensordescriptor)、[ISkillFeatureImageDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeatureimagedescriptor)、および [ISkillFeatureMapDescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturemapdescriptor))。 これらの[Isたり Featuredescriptor](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor)の派生元は、記述する[Isて featurevalue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue)オブジェクトのファクトリオブジェクトとしても機能します。

インスタンス化時に、 [Iskillfeaturevalue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturevalue)に割り当てるために使用されるプリミティブが、その[Iskillfeaturevalue](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeaturedescriptor)によって提供される記述と一致しない場合、各型に固有の自動変換がシームレスに行われる可能性があります (たとえば、イメージを必要な形式とは異なる形式でバインドする場合、または縦横比が異なる場合にトリミングする場合などです。

## API フロー<a name="APIFlow"></a>

すべてのスキルは[SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview)から同じ基本インターフェイスのセットを派生させるため、これらはすべて同じフローに従い、通常は次の操作に分類されます。

<div style="text-align:center" markdown="1">

![Windows ビジョンスキル API のフロー図アプリケーションからの API 呼び出しの通常のシーケンスを示す取り込み Windows ビジョンスキル](../images/vision-skills-flow.png)

</div>

1) [Isの記述子](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor)の派生をインスタンス化します。

2) 手順 1. のインスタンスを使用して ( [GetSupportedExecutionDevicesAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.getsupportedexecutiondevicesasync)を使用して) 使用可能な実行デバイスを照会するか、手順 3. をスキップして直接試行します。

3) 手順 1. のインスタンスと手順 2. の目的の実行デバイス (isを使用した) を使用して、スキルをインスタンス化し[ます (isを使用します。](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync) [Isの記述子。 CreateAsync ()](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskilldescriptor.createskillasync))。

4) 手順 3. のスキルインスタンスを使用して、スキルバインドオブジェクトをインスタンス化します ( [Iskill](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.createskillbindingasync)を使用します)。

5) アプリケーションからプリミティブ ([Videoframe](https://docs.microsoft.com/uwp/api/windows.media.videoframe)、 [IVectorView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.ivectorview_t_)、 [IMapView](https://docs.microsoft.com/uwp/api/windows.foundation.collections.imapview_k_v_)など) を取得し、手順 4. のバインドオブジェクトにバインドします (名前を使用してインデックス付けされた対応する[is 機能](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)にアクセスし、を呼び出します)。[SetFeatureValueAsync (Object)](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.setfeaturevalueasync))。

6) ( [Iskill. EvaluateAsync](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskill.evaluateasync)を呼び出すことによって) バインドオブジェクトに対してスキルを実行します。

7) 手順 4. でインスタンス化されたバインディングオブジェクトから出力プリミティブを取得します (名前を使用してインデックスが付けられた対応する[isに](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature)アクセスし、getter[値](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview.iskillfeature.featurevalue)を呼び出します)。

8) Rinse を実行し、同じバインドオブジェクトと新しいプリミティブを使用して手順 5. を繰り返します。

これを実際に確認するには、「[アプリからの Windows ビジョンスキル](tutorial1.md)の取り込み」のチュートリアルを参照してください。

[!INCLUDE [help](../includes/get-help-vision.md)]
