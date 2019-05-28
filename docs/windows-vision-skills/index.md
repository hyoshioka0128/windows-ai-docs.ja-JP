---
author: eliotcowley
title: Windows Vision Skills
description: Windows Vision Skills API について説明します。
ms.author: elcowle
ms.date: 4/25/2019
ms.topic: article
keywords: Windows 10, Windows AI, Windows ML, WinML, Windows Machine Learning, Windows Vision Skills
ms.localizationpriority: medium
ms.openlocfilehash: 7426688304b59fb429180a1a0046b6d4be1c06d5
ms.sourcegitcommit: 6948f383d671a042290d4ef83e360fa43292eef2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66179773"
---
# <a name="windows-vision-skills-preview"></a>Windows Vision Skills (プレビュー)

> [!NOTE]
> 一部の情報はリリース前の製品に関する事項であり、正式版がリリースされるまでに大幅に変更される可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

効率的な機械学習ソリューションとコンピューター ビジョン ソリューションを実装して統合することは、開発者にとって負担のかかるタスクです。 業界は速いペースで変化し、カスタムメイドのソリューションが大量に発生しているため、アプリケーション開発者は変化について行くのに懸命です。 既存の API と低レベルのフレームワークがあれば、これらのソリューションを開発者が効果的に活用する前に行う学習が簡単になります。

**Windows Vision Skills** フレームワークは、コンピューター ビジョンを利用しやすくするためのものです。 これは、ローカル デバイス上で実行されている、Windows アプリケーション内で使用するコンピューター ビジョン モジュールの配置方法を標準化します。 これにより、複雑なしくみが、標準化されたプリミティブを使用した単一のプログラミング パラダイムに抽象化されるため、開発者は優れたコンピューター ビジョン アプリケーションの構築に集中できます。

![Windows Vision Skills が開発スタック内のどこに該当するかを示す図。最下部レイヤー (GPU、CPU、VPU など) から始まり、その上にハードウェア アクセラレータ フレームワーク (DirectX、DirectML など) が存在し、次のレイヤーは Windows API およびサードパーティ フレームワークで構成される Windows Vision Skills API で、最上位レイヤーは UWP、.NET Core、および Win32 アプリケーションで構成されます](../images/vision-skills-diagram2-wide.png)

複雑な詳細を含む実装は、[Microsoft.AI.Skills.SkillInterfacePreview](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview) 名前空間内の基本クラスおよびインターフェイスを継承する拡張可能な WinRT API によってカプセル化されています。 この API は、すべての種類の Windows アプリ (UWP、.NET Core、および Win32) が取り込むことができます。 このフレームワークは、このフレームワーク上に構築するすべての開発者に公開されています。

* [NuGet パッケージを取得する](https://www.nuget.org/packages/Microsoft.AI.Skills.SkillInterfacePreview/)

## <a name="what-is-a-skill"></a>*スキル*とは

Windows Vision Skills のコンテキストで、スキルとは、入力を処理して出力を生成する効率的なモジュール型のコードです。 スキルは、単一目的のマイクロスキルを使用したエッジ検出のような単純な機能や、スケルトンの検出などの複雑な問題に対処するシナリオ スキルを形成する豊富な機能のセットをカプセル化できます。

## <a name="benefits"></a>利点

- **単純な統合**:スキルにより、機械学習やコンピューター ビジョンの専門知識、あるいは Windows の低レベル API についての事前知識が不要なそのまま使用できる API を使用して、機能をアプリケーションに容易に追加できるようになります。

- **ハードウェア アクセラレータの抽象化**:Windows Vision Skills フレームワークはハードウェア資産のクエリを実行し、OS プロビジョニングを行うため、開発者は実行時にコンピューティングの決定を効率的に行うことができます。

- **相互運用性**:このフレームワークは、カメラや写真、ビデオからの画像プリミティブなどの資産や OS インターフェイスと連携し、[Windows Machine Learning API](../windows-ml/index.md) と組み合わせて使用できます。

- **NuGet パッケージ**:Windows Vision Skills では、既存のアプリケーションを破壊せずに簡単に反復するために厳密なバージョン管理を行います。 これらは取り込みや更新が簡単で、ライセンスを通じて知的財産を保護します。

- **拡張性**:このフレームワークは、**OpenCV** などの既存の機械学習フレームワークおよびライブラリと連携するために簡単に拡張できます。

- **モジュール方式**:スキルは複雑なシナリオに対処するためのレシピのように、アプリケーション内で連続的につなぎ合わせることができます。 また、開発者はスキルを 1 つのパッケージにバンドルすることもできます。

このプレビューでは視覚寄りのシナリオとプリミティブに焦点を絞っていますが、この API はオーディオ処理やテキスト処理などを可能にするさまざまな入力および出力変数に対応するようになっています。

## <a name="see-also"></a>関連項目

- [Windows Vision Skills NuGet パッケージ](https://www.nuget.org/profiles/VisionSkills)

- [GitHub のサンプル](https://github.com/Microsoft/WindowsVisionSkillsPreview)

- [API リファレンス](https://docs.microsoft.com/dotnet/api/microsoft.ai.skills.skillinterfacepreview)

[!INCLUDE [help](../includes/get-help-vision.md)]
