---
title: 認定済みの Power BI カスタム ビジュアル
description: 認定のためにカスタム ビジュアルを送信する場合の要件とプロセス。 認定済みのカスタム ビジュアルの一覧。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/21/2018
ms.openlocfilehash: 812ac76266f8ef3299fa72b575c9ff68d2e75a79
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216357"
---
# <a name="certified-custom-visuals"></a>認定済みカスタム ビジュアル

## <a name="what-are-certified-custom-visuals"></a>**_認定済み_** カスタム ビジュアルとは何ですか?

認定済みカスタム ビジュアルとは**マーケットプレース**内のビジュアルであり、**特定のコード**要件を満たしていることを **Microsoft Power BI チーム**がテストし、承認したものです。 カスタム ビジュアルが認定されると、機能が増えます。 たとえば、[PowerPoint にエクスポート](consumer/end-user-powerpoint.md)したり、ユーザーが[レポート ページを定期購読する](consumer/end-user-subscribe.md)と受信するメールにビジュアルを表示したりできます。

**認定済みカスタム ビジュアル**は[標準カスタム ビジュアル](power-bi-custom-visuals.md)のように使用されます。 認定済みカスタム ビジュアルは、**Power BI サービス** (**Power BI Desktop レポート**) に追加し、**Power BI Mobile** や **Power BI Embedded** で表示できます。

実行されたテストは、ビジュアルが外部のサービスやリソースにアクセスしないことを確認するように作られています。 **Microsoft** はサードパーティ製のカスタム ビジュアルの作成者では*ありません*。サードパーティ製のビジュアルの機能については、作成者に直接お問い合わせいただくことをお客様にお勧めしています。

認定プロセスは任意のプロセスであり、マーケットプレースのビジュアルを認定してもらうかどうかは開発者次第です。  

**認定されていないカスタム ビジュアル**が安全ではないとは限りません。 一部のビジュアルは 1 つまたは複数の[認定要件](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)を満たしていないために認定されていません。 たとえば、地図ビジュアルのような外部サービスや商用ライブラリを利用するビジュアルに接続する場合です。

独自の視覚エフェクトを作成して  **[Microsoft AppSource](https://appsource.microsoft.com)** に追加することに興味がある Web 開発者の方は、  **[Power BI カスタム ビジュアルを開発する](developer/custom-visual-develop-tutorial.md)** 方法に関するページをご覧ください。

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Power BI の認定済みのカスタム ビジュアルの削除

マイクロソフトは独自の裁量で[認定リスト](#list-of-custom-visuals-that-have-been-certified)からビジュアルを削除できます。

## <a name="getting-a-custom-visualcertified"></a>カスタム ビジュアルの認定を受ける

### <a name="certification-requirements"></a>認定要件

[カスタム ビジュアルを認定してもらう](#certified-custom-visuals)には、カスタム ビジュアルが以下の基準を満たしている必要があります。  

* Microsoft AppSource が承認していること。 カスタム ビジュアルは Microsoft の[マーケットプレース](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)に表示されるはずです。
* カスタム ビジュアルがバージョン管理された API 1.2 以降で記述されていること。
* Power BI チームがレビューするためのコード リポジトリが用意されていること (たとえば、GitHub に人間が読める形式のソース コード (JavaScript や TypeScript) を用意しておきます)。

    >[!Note]
    > Github でコードを一般公開する必要はありません。

* 公開レビュー可能な OSS コンポーネントのみを使用すること (一般公開の JS ライブラリまたは TypeScript。 ソース コードがレビューできて、既知の脆弱性がない)。 Microsoft は商用コンポーネントを利用してカスタム ビジュアルを検証することかできません。

* 外部のサービスやリソースにアクセスしない。これには HTTP/S 要求や WebSocket 要求を Power BI から外部のサービスに送信できないことが含まれますが、それに限定されません。 

> [!TIP]
> 送信する前に、EsLint と既定のセキュリティ ルールセットを使用して、コードを事前検証することをお勧めします。

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>認定のためにカスタム ビジュアルを送信するプロセス

認定のためにカスタム ビジュアルを送信するには、次の手順に従います。

1. Power BI カスタム ビジュアルのサポート チーム (pbicvsupport@microsoft.com) に電子メールを送信します。 電子メールには、次の情報を含めます。
    * 件名:ビジュアル認定の要求
    * 人間が読めるソース コードがホストされている GitHub リポジトリへのリンク
    * [要件の遵守](#certification-requirements)
    * コード レビューに合格する

2. カスタム ビジュアルが認定され、[認定リスト](#list-of-custom-visuals-that-have-been-certified)に追加されたら、あるいは却下され、修正すべき問題が報告されたら、Microsoft カスタム ビジュアル チームから通知が届きます。 Microsoft との連絡手段を維持し、必要に応じて認定済みのビジュアルを更新するのは、開発者の責任です。

## <a name="list-of-custom-visuals-that-have-been-certified"></a>認定されているカスタム ビジュアルの一覧

| AppSource へのリンク | 動画のリンク |
| --- | --- |
| [3AG Systems - 相対差異を含む縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [高度なドーナツ ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [高度なネットワークのビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [高度な時系列ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [高度なコンボ ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [アスター プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft カレンダー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [MAQ Software による Bowtie Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [ビデオ](https://youtu.be/So5xKMSpVJI) |
| [箱ひげ図](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [MAQ Software による箱ひげ図](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [ビデオ](https://youtu.be/JoHaFLfhXdo) |
| [MAQ Software によるブリック グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [ビデオ](https://youtu.be/hA3DOsvn2xY) |
| [Akvelon によるバブル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [箇条書きのグラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [ビデオ](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz (OKViz による箇条書きグラフ)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [ビデオ](https://youtu.be/mtvUNl9bMjA) |
| [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [OKViz によるローソク足](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [ビデオ](https://youtu.be/nT_18gyRxPo) |
| [OKViz の Card with States](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer (Chiclet スライサー)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [弦](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [ビデオ](https://youtu.be/AQvd2FhRyCI) |
| [MAQ Software による円形ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [ビデオ](https://youtu.be/9NHXALkBXuY) |
| [クラスター マップ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [MAQ Software による円筒ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [ビデオ](https://youtu.be/DgdoWi7Gcxo) |
| [ダイヤル ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [ドット プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Dot Plot by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [ビデオ](https://youtu.be/By16pX9KT40) |
| [ドリルダウン カルトグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [ドリルダウン コロプレス](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [ドリル ダウン縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [ビデオ](https://youtu.be/lBy2gQQ5YsQ) |
| [時間基準データのドリルダウン縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [ビデオ](https://youtu.be/T_mRou18vx0) |
| [ドリルダウン ドーナツ グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [ビデオ](https://youtu.be/AUVFrSHmPeo) |
| [デュアル KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [MAQ ソフトウェアによる動的なツールヒント](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [ビデオ](https://youtu.be/Z-tl97BpEr0) |
| [強化された散布図](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [ビデオ](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten スタック シャッフル](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten ワッフル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Devscope による一覧でのフィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [ビデオ](https://youtu.be/RetEWGwBu0I) |
| [力指向グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [ビデオ](https://youtu.be/YsTa7uyJ4sg) |
| [MAQ Softwareによるソースでのじょうご](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [ビデオ](https://youtu.be/R_EcimsLI8U) |
| [ガント](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [ビデオ](https://youtu.be/qJ7s_KrGiUU) |
| [MAQ Software による Gantt Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [ビデオ](https://youtu.be/vJLV9JRCpI8) |
| [地球データ バー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [MAQ ソフトウェアによるグリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [ビデオ](https://youtu.be/VOPoDJgZfOY) |
| [Akvelon による階層グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [ビデオ](https://youtu.be/0ZGzJaq_KT4) |
| [ヒストグラム グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [MAQ Software によるポイント付きヒストグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [ビデオ](https://youtu.be/-ILF--wExrw) |
| [MAQ Software による水平方向のじょうご](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [ビデオ](https://youtu.be/SudZei68PPo) |
| [CloudScope によるイメージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [イメージ グリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [インフォグラフィック デザイナー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [Akvelon による KPI グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [MAQ Software による KPI 列](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [ビデオ](https://youtu.be/rU0xoOlIq1U) |
| [MAQ Software による KPI グリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [ビデオ](https://youtu.be/dM4PvZh71V0) |
| [KPI インジケーター](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [MAQ Software による KPI ティッカー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [ビデオ](https://youtu.be/cudG4gsZ2V8) |
| [MAQ Software による線形ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [ビデオ](https://youtu.be/7_jFaM30dkc) |
| [LineDot グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Mekko グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [ビデオ](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [CloudScope による概要](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Play Axis (動的スライサー)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [ビデオ](https://youtu.be/IvfIP3E6-1Q) |
| [累乗 KPI マトリックス](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [ビデオ](https://youtu.be/1enze8pcGzY) |
| [パルス グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [ビデオ](https://youtu.be/DQWdcQtjDVw) |
| [MAQ Software による四分割グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [ビデオ](https://youtu.be/ppBnyhqWNC0) |
| [Radar chart (レーダー チャート)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [MAQ Software によるリング グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [ビデオ](https://youtu.be/pDToHDFHnq8) |
| [MAQ Software による回転グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [ビデオ](https://youtu.be/d5xBCMmb3hU) |
| [Sankey グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [ビデオ](https://youtu.be/WWP9wVUHGaA) |
| [Akvelon による散布図](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [スクローラー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz (OKViz でのスマート フィルター)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [ビデオ](https://youtu.be/gcJsDDRQq28) |
| [OKViz によるスパークライン](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [ビデオ](https://youtu.be/0m3Vnvso9tY) |
| [ストリーム グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [OKViz によるシノプティック パネル](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [テーブル ヒートマップ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [回転速度計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [ビデオ](https://youtu.be/C3OXdETbS9o) |
| [テキスト フィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [MAQ ソフトウェアによるテキスト ラッパー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [MAQ Software による温度計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [ビデオ](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [タイムライン スライサー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [ビデオ](https://youtu.be/ozMtZ4_NZ10) |
| [CloudScope によるタイムライン](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [ビデオ](https://youtu.be/szNi9YgXFJc) |
| [トルネード チャート](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [ビデオ](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [MAQ Software による取引グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [ビデオ](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate の差異](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [ビデオ](https://youtu.be/pDYF8iZxERs) |
| [Ultimate のウォーターフォール](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [ビデオ](https://youtu.be/0BZsVCQdEkc) |
| [CloudScope によるユーザー一覧](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [ワッフル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [ビデオ](https://youtu.be/1vRqYUsm3Vk) |
| [ワード クラウド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [ビデオ](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>次の手順

* [Power BI カスタム ビジュアルの開発](developer/custom-visual-develop-tutorial.md)
* [YouTube の Microsoft カスタム ビジュアル プレイリスト](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI での視覚化](visuals/power-bi-report-visualizations.md)  
* [Power BI でのカスタム ビジュアル](power-bi-custom-visuals.md)  
* [Microsoft AppSource へのカスタム ビジュアルの公開](developer/office-store.md)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
