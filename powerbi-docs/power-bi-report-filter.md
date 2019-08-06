---
title: Power BI レポートの新しいフィルター エクスペリエンス
description: Power BI のフィルターに、新しい機能と新しいデザインが追加されます。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/18/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 148f4881f78b5bba9b6936f5688ba6aaea3a0145
ms.sourcegitcommit: dc0258bb4f647ff646c6fff2aaffa29b413aa2df
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68346363"
---
# <a name="the-new-filter-experience-in-power-bi-reports"></a>Power BI レポートの新しいフィルター エクスペリエンス

Power BI のフィルターに、新しい機能と新しいデザインが追加されました。 新しいフィルター エクスペリエンスを利用するとき、レポートの他の部分に合わせて [フィルター] ウィンドウを書式設定できます。 フィルターをロックし、非表示にすることも可能です。 レポートをデザインするとき、[視覚化] ウィンドウには、以前の [フィルター] ウィンドウは表示されません。 フィルターの編集と書式設定のすべての操作を、1 つの [フィルター] ウィンドウで行います。 

![新しいフィルター エクスペリエンス](media/power-bi-report-filter/power-bi-filter-reading.png)

レポート デザイナーが、新しい 1 つの [フィルター] ウィンドウで実行できる操作を次に示します。

- フィルターを適用するフィールドを追加および削除する。 
- フィルターの状態を変更する。
- レポートの一部と感じられるように [フィルター] ウィンドウを書式設定およびカスタマイズする。
- コンシューマーがレポートを開くときに、フィルター ウィンドウは既定で開いているのか、折りたたまれているのかを定義する。
- [フィルター] ウィンドウ全体、またはレポートのコンシューマーに表示させたくない特定のフィルターを非表示にする。
- 新しい [フィルター] ウィンドウの表示、開く、折りたたむなどの状態を制御し、ブックマークする。
- コンシューマーに編集させたくないフィルターをロックする。

新しいフィルター エクスペリエンスにより、レポート コンシューマーがビジュアルをポイントして、そのビジュアルに影響を及ぼすフィルターまたはスライサーの一覧を読み取り専用で表示することもできます。

![ビジュアルのフィルターの一覧](media/power-bi-report-filter/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>新しいフィルター エクスペリエンスを有効にする 

新しいレポートでは、新しいフィルター エクスペリエンスが既定で有効になっています。 Power BI Desktop または Power BI サービスで既存のレポートに対して新しいエクスペリエンスを有効にすることができます。

### <a name="turn-on-new-filters-for-an-existing-report-in-power-bi-desktop"></a>Power BI Desktop で既存のレポートに対して新しいフィルターを有効にする

1. Power BI Desktop の既存のレポート内で、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]** を選択します。
2. 左側のナビゲーション バーで、 **[現在のファイル]** の **[レポートの設定]** を選択します。
3. **[エクスペリエンスのフィルター処理]** の下で、 **[このレポートに関して、更新されたフィルター ウィンドウを有効にし、ビジュアル ヘッダーにフィルターを表示する]** を選択します。

### <a name="turn-on-new-filters-for-an-existing-report-in-the-service"></a>サービスで既存のレポートに対して新しいフィルターを有効にする

1. Power BI サービスで、ワークスペースのコンテンツ リストで **[レポート]** タブを選択します。
2. 有効にするレポートを見つけて、そのレポートの **[設定]** アイコン ![レポートの設定アイコン](media/power-bi-report-filter/power-bi-settings-icon.png) を選択します。
3. **[エクスペリエンスのフィルター処理]** の下で、 **[このレポートに関して、更新されたフィルター ウィンドウを有効にし、ビジュアル ヘッダーにフィルターを表示する]** を選択します。

    ![更新されたフィルター ウィンドウを有効にする](media/power-bi-report-filter/power-bi-service-filter-enable.png)

## <a name="view-filters-for-a-visual-in-reading-mode"></a>閲覧モードでビジュアルのフィルターを表示する

閲覧モードでは、ビジュアルのフィルター アイコンにカーソルを合わせると、そのビジュアルに影響を与えているすべてのフィルターやスライサーなどを含むポップアップ フィルター リストが表示されます。 ポップアップ フィルター リストの書式設定は、[フィルター] ウィンドウの書式設定と同じです。 

![ビジュアルに影響を与えているフィルター](media/power-bi-report-filter/power-bi-filter-per-visual.png)

このビューに表示されるフィルターの種類は次のとおりです。 
- 基本フィルター
- スライサー
- クロス強調表示 
- クロス フィルター処理
- 高度なフィルター
- 上位 N のフィルター
- 相対日付フィルター
- 同期スライサー
- 含める/除外するフィルター
- URL を使って渡されるフィルター

## <a name="build-the-new-filters-pane"></a>新しい [フィルター] ウィンドウを構築する

新しい [フィルター] ウィンドウを有効にすると、そのウィンドウはレポート ページの右側に表示されます。既定では、これは現在のレポートの設定に基づいて書式設定されます。 新しい [フィルター] ウィンドウを使って、適用するフィルターを構成したり、既存のフィルターを更新したりします。 新しい [フィルター] ウィンドウには、公開したレポートがレポートのコンシューマーにどのように表示されるかが示されます。 

1. 既定では、レポート コンシューマーは [フィルター] ウィンドウを表示できます。 表示されないようにするには、 **[フィルター]** の横にある目のアイコンを選択します。

    ![Power BI フィルターの目のアイコン](media/power-bi-report-filter/power-bi-filter-eye.png)

2. 新しい [フィルター] ウィンドウを構築し始めるには、目的のフィールドを、ビジュアル、ページ、レポートのいずれかのレベルのフィルターとして、新しい [フィルター] ウィンドウにドラッグします。

レポート キャンバスにビジュアルを追加すると、Power BI によって、ビジュアル内の各フィールドの [フィルター] ウィンドウにフィルターが自動的に追加されます。 

## <a name="lock-or-hide-filters"></a>フィルターのロックまたは非表示

個別のフィルター カードをロックしたり非表示にしたりすることができます。 フィルターをロックすると、レポートのコンシューマーはそれを表示できますが、変更はできません。 これを非表示にすると、表示もされなくなります。 フィルター カードの非表示は、null 値や予期しない値を除外する、データのクリーンアップ用フィルターを非表示にする必要がある場合に、特に便利です。 

- 新しい [フィルター] ウィンドウで、フィルター カード内にある **[フィルターをロックします]** または **[フィルターの非表示]** アイコンを選択または選択解除します。

   ![フィルターの非表示またはロック](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

新しい [フィルター] ウィンドウでこれらの設定のオンとオフを切り替えると、レポートに変更が反映されるのを確認できます。 非表示のフィルターは、ビジュアルに対するポップアップ フィルター リストには表示されません。

また、新しい [フィルター] ウィンドウの状態を構成して、レポートのブックマークで満たすことも可能です。 ウィンドウを開いた状態、閉じた状態、および表示の状態は、すべてブックマーク可能です。
 
## <a name="format-the-new-filters-pane"></a>新しいフィルター ウィンドウを書式設定する

この新しいエクスペリエンスの大きな割合を占めるのは、レポートのルック アンド フィールと一致するように [フィルター] ウィンドウを書式設定できることです。 レポート内のページごとに異なる方法で [フィルター] ウィンドウを書式設定できます。 書式設定できる要素は次のとおりです。 

- 背景色
- 背景の透明度
- 境界線のオンまたはオフ
- 境界線の色
- タイトルとヘッダーのフォント、色、テキスト サイズ

また、フィルター カードに対しても、それが適用されている (何かに設定されている) か、または使用可能 (オフ) かに応じて、これらの要素を書式設定することができます。 

- 背景色
- 背景の透明度
- 境界線: オンまたはオフ
- 境界線の色
- フォント、色、テキスト サイズ
- 入力ボックスの色

### <a name="format-the-filters-pane-and-cards"></a>[フィルター] ウィンドウとカードを書式設定する

1. レポート内で、レポート自体か背景 ("*壁紙*") をクリックしてから、 **[視覚化]** ウィンドウ内で **[書式]** を選択します。 
    レポート ページや壁紙、また [フィルター] ウィンドウやフィルター カードを書式設定するためのオプションが表示されます。

    ![書式設定アイコンを選択する](media/power-bi-report-filter/power-bi-filter-format.png)    

1. **[フィルター ウィンドウ]** を展開して背景、アイコン、左の境界線の色を設定し、レポート ページを補完します。

    ![フィルター ウィンドウを展開する](media/power-bi-report-filter/power-bi-filter-format-pane-font.png)

1. **[フィルター カード]** を展開して、色と境界線の **[使用可能]** と **[適用済み]** を設定します。 カードのさまざまな色を使用可能にして適用すれば、どのフィルターが適用されているか明確になります。 
  
    ![フィルター カードを展開する](media/power-bi-report-filter/power-bi-filter-format-card-font.png)

## <a name="theming-for-filter-pane"></a>[フィルター] ウィンドウのテーマ
テーマ ファイルを使用して、[フィルター] ウィンドウの既定の設定を変更できるようになりました。 作業を開始するためのサンプル テーマのスニペットを次に示します。

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filter-pane"></a>フィルター ウィンドウを並べ替える

カスタムの並べ替え機能は、新しいフィルター ウィンドウのエクスペリエンスの一部です。 レポート作成者がフィルターをドラッグ アンド ドロップして、必要な順序で並べ替えることができます。

![フィルターの並べ替え順序を変更する](media/power-bi-report-filter/power-bi-filter-sort.gif)

フィルターの既定の並べ替え順序はアルファベット順です。 カスタムの並べ替えモードを開始するには、任意のフィルターを新しい位置にドラッグします。 フィルターは、ビジュアル レベル、ページ レベル、レポート レベルなど、フィルターの適用先のレベル内でのみ並べ替えることができます。

## <a name="improved-filters-pane-accessibility"></a>[フィルター] ウィンドウのアクセシビリティの向上

新しい [フィルター] ウィンドウのキーボード操作が向上しました。 [フィルター] ウィンドウのすべての部分を Tab キーを使って移動できるほか、キーボードのコンテキスト キーまたは Shift + F10 キーでコンテキスト メニューを開くことができます。

![[フィルター] ウィンドウのアクセシビリティ](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>フィルターの名前を変更する
[フィルター] ウィンドウを編集している場合、タイトルを編集するには、そのタイトルをダブルクリックします。 名前の変更は、エンド ユーザーが理解しやすいようにフィルター カードを更新したいときに便利です。 フィルター カードの名前を変更しても、フィールド一覧のフィールドの表示名は "*変更されない*" ことに注意してください。 この操作では、フィルター カードで使用される表示名が変更されるだけです。

![フィルターの名前を変更する](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>フィルターの種類への変更を制限する

レポート設定のフィルター処理エクスペリエンスのセクションには、ユーザーがフィルタ―の種類を変更できるようにするかどうかを制御するオプションがあります。

![フィルターの種類の変更を制限する](media/power-bi-report-filter/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>次の手順

新しいフィルター エクスペリエンスをお試しください。 この機能のフィードバックや、機能改善を続けていくための方法に関するご意見については、[Power BI のアイデア サイト](https://ideas.powerbi.com/forums/265200-power-bi)からお寄せください。 

- [レポート フィルターの使用方法](consumer/end-user-report-filter.md)
- [レポート内のフィルターと強調表示](power-bi-reports-filters-and-highlighting.md)
- [Power BI で使用できるさまざまなフィルター](power-bi-report-filter-types.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
