---
title: Power BI の視覚化の書式を設定する
description: 視覚化タイトル、背景、および凡例のカスタマイズ
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 011e2b6d3bf5cc998f7db76e96536d2ddab09888
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880865"
---
# <a name="customize-visualization-titles-legends-and-backgrounds"></a>視覚化のタイトル、凡例、および背景をカスタマイズする

このチュートリアルでは、視覚化をカスタマイズする、さまざまな方法について説明します。 視覚化をカスタマイズするオプションは多数あります。 そのすべてを学習するには、 **[形式]** ウィンドウ (ペイント ローラー アイコンを選択) を調べることをお勧めします。 その手始めとして、この記事では視覚化のタイトル、凡例、背景をカスタマイズする方法を説明します。

一部の視覚化についてはカスタマイズできません。 詳細については、[完全なリスト](#visualization-types-that-you-can-customize)をご覧ください。

4 分 50 秒までビデオを早送りして、視覚化をカスタマイズする方法をご覧いただくことができます。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

ここでは以下の手順に従って、ご自分のデータでやってみてください。

## <a name="prerequisites"></a>前提条件

- Power BI サービスまたは Power BI Desktop

- 小売りの分析のサンプル レポート

## <a name="customize-visualization-titles-in-reports"></a>レポートの視覚エフェクトのタイトルをカスタマイズする

まず、[Power BI サービス](https://app.powerbi.com)にサインインし、[小売りの分析のサンプル](../sample-datasets.md) レポートを[レポート編集](../service-interact-with-a-report-in-editing-view.md)ビューで開きます。

> [!NOTE]
> 視覚エフェクトをダッシュボードにピン留めすると、その視覚エフェクトはダッシュボード タイルになります。 タイル自体も、[新しいタイトルとサブタイトル、ハイパーリンク、およびサイズの変更](../service-dashboard-edit-tile.md)でカスタマイズできます。

1. **小売りの分析のサンプル** レポートの **[新しいストア]** ページに移動します。

1. "**開店月別、チェーン別の開店店舗数**" 集合縦棒グラフを選択します。

1. **[視覚化]** ウィンドウで、ペイントローラー アイコンを選択して、形式オプションを表示します。

1. **[タイトル]** を選択してセクションを展開します。

   ![[形式] ウィンドウ、ペイント ローラー アイコン、および [タイトル] ドロップダウンを指している矢印のスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/power-bi-formatting-menu.png)

1. **[タイトル]** スライダーを **[オン]** にします。

   ![オンのスライダーのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/onoffslider.png)

1. タイトルを変更するには、 **[タイトル テキスト]** フィールドに「*月別の開店した店舗数*」と入力します。

1. **[フォント色]** をオレンジに、 **[背景色]** を黄色に変更します。

    1. ドロップダウンを選択し、 **[テーマの色]** 、 **[最近使用した色]** 、または **[ユーザー設定の色]** から色を選択します。

        ![フォントの色と背景色のオプションのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/customizecolorpicker.png)

    1. ドロップダウンを選択して、色ウィンドウを閉じます。

       変更を保存します。

       すべての変更を既定値の戻す必要がある場合は、色ウィンドウの **[既定値に戻す]** を選択します。

1. テキスト サイズを **12 ポイント**に増やします。

1. 最後のカスタマイズとして、グラフのタイトルを視覚化の中央に配置します。

    ![[中央揃え] オプションが選択されている [配置] コントロールのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/customizealign.png)

チュートリアルのこの時点で、集合縦棒グラフのタイトルは次のように表示されます。

![新しく構成された集合縦棒グラフのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/tutorialprogress1.png)

変更を保存して、次のセクションに移動します。

すべての変更を既定値に戻す必要がある場合は、 **[タイトル]** カスタマイズ ウィンドウの下部にある **[既定値に戻す]** を選択します。

![[既定値に戻す] オプションのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/revertall.png)

## <a name="customize-visualization-backgrounds"></a>視覚エフェクトの背景をカスタマイズする

同じ集合縦棒グラフを選択して、 **[背景]** オプションを展開します。

1. **[背景]** スライダーを **[オン]** にします。

1. ドロップダウン リストを選択し、灰色を選択します。

1. **[透明度]** を **[74%]** に変更します。

チュートリアルのこの時点で、集合縦棒グラフの背景は次のように表示されます。

![背景色が更新された集合縦棒グラフのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/power-bi-customize-background.png)

変更を保存して、次のセクションに移動します。

すべての変更を既定値に戻す必要がある場合は、 **[背景]** カスタマイズ ウィンドウの下部にある **[既定値に戻す]** を選択します。

## <a name="customize-visualization-legends"></a>視覚エフェクトの凡例をカスタマイズする

1. **[概要]** レポート ページを開き、"**年度別および地域マネージャー別の総売上差異**" グラフを選択します。

1. **[視覚化]** タブで、ペイント ローラー アイコンを選択して、[形式] ウィンドウを開きます。

1. **[凡例]** オプションを展開します。

      ![[凡例] オプションのスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/legend.png)

1. **[凡例]** スライダーを **[オン]** にします。

1. 凡例を視覚エフェクトの左側に移動します。

1. **[タイトル]** を **[オン]** に切り替えて、凡例にタイトルを追加します。

1. *[凡例名]* テキスト フィールドに 「**マネージャー**」と入力します。

チュートリアルのこの時点で、集合縦棒グラフの凡例は次のように表示されます。

![集合縦棒グラフの更新された凡例のスクリーンショット。](media/power-bi-visualization-customize-title-background-and-legend/legend-move.png)

変更を保存して、次のセクションに移動します。

すべての変更を既定値に戻す必要がある場合は、 **[凡例]** カスタマイズ ウィンドウの下部にある **[既定値に戻す]** を選択します。

## <a name="visualization-types-that-you-can-customize"></a>カスタマイズ可能な視覚化の種類

視覚化と、各視覚化で使用できるカスタマイズ オプションの一覧を次に示します。

| 視覚化 | タイトル | 背景 | 凡例 |
|:--- |:--- |:--- |:--- |
| 面 | はい | はい |はい |
| 横棒 | はい | はい |はい |
| カード | はい | はい |該当なし |
| 複数行カード | はい | はい | 該当なし |
| 列 | はい | はい | はい |
| 複合 | はい | はい | はい |
| ドーナツ | はい | はい | はい |
| 塗り分け地図 | はい | はい | はい |
| じょうごグラフ | はい | はい | 該当なし |
| ゲージ | はい | はい | 該当なし |
| KPI | はい | はい | 該当なし |
| 折れ線 | はい | はい | はい |
| マップ | はい | はい | はい |
| Matrix | はい | はい | 該当なし |
| 円 | はい | はい | はい |
| 散布 | はい | はい | はい |
| スライサー | はい | はい | 該当なし |
| テーブル | はい | はい | 該当なし |
| テキストボックス | いいえ | はい | 該当なし |
| ツリーマップ | はい | はい | はい |
| ウォーターフォール | はい | はい | はい |

## <a name="next-steps"></a>次の手順

- [X 軸と Y 軸のプロパティのカスタマイズ](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [色の書式設定と軸のプロパティの概要](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Power BI サービス コンシューマーの基本的な概念](../consumer/end-user-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
