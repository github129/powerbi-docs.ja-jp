---
title: Power BI サービスから印刷する
description: Power BI からダッシュボード、タイル、またはレポート ページを印刷します。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 5540ef52109ab593e834cb446c3442093d4d94f3
ms.sourcegitcommit: a054782370dec56d49bb205ee10b7e2018f22693
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2019
ms.locfileid: "56661861"
---
# <a name="printing-from-power-bi-service"></a>Power BI サービスからの印刷
Power BI サービスから、ダッシュボード全体、ダッシュボード タイル、レポート ページ、またはレポートのビジュアルを印刷します。 レポートは、一度に 1 ページのみを印刷できます。レポート全体を一度に印刷することはできません。

> [!NOTE]
> 印刷は、Power BI サービスでのみ利用できます。Power BI Desktop では利用できません。
> 
> 

次のビデオで、ダッシュボードとレポートから印刷する方法をご覧ください。 その後、ビデオで説明されている手順に従って、ご自分でやってみてください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/jtlLGRKBvXY" frameborder="0" allowfullscreen></iframe>

## <a name="print-a-dashboard"></a>ダッシュボードの印刷
1. 印刷するダッシュボードを開きます。
2. 右上隅で省略記号 (...) を選択し、 **[ダッシュボードを印刷]** を選択します。
   
    ![[ダッシュボードを印刷] オプション](./media/end-user-print/pbi_print_dash_ellipses.png)
3. お使いのブラウザーの [印刷] ウィンドウが開きます。 設定と出力先を選択して、 **[印刷]** を選択します。
   
   > [!NOTE]
   > 表示される印刷ダイアログ ボックスは、お使いのブラウザーによって異なります。
   > 
   
    ![[印刷] ダイアログ](./media/end-user-print/pbi_print_dash_new2.png)

## <a name="print-a-dashboard-tile"></a>ダッシュボード タイルの印刷
1. 省略記号を選んでフォーカス アイコン ![フォーカス アイコン](./media/end-user-print/power-bi-focus-icon.png) を選び、[タイルをフォーカス モードで開きます](end-user-focus.md)。
   
    ![省略記号メニュー](./media/end-user-print/menu-options.png)
2. 上部ナビゲーション バーの全画面表示アイコン ![全画面表示アイコン](./media/end-user-print/power-bi-full-screen-icon.png) を選ぶことにより、[全画面表示モード](end-user-focus.md)でタイルを開きます。
3. タイルの上にカーソルを移動して、[オプション] メニューを表示します。
   
    ![全画面表示オプション メニュー](./media/end-user-print/menu-options-new.png)
4. [印刷] アイコン ![[印刷] アイコン](./media/end-user-print/print-icon.png) を選びます。     
   
   > [!NOTE]
   > 表示される印刷ダイアログ ボックスは、お使いのブラウザーによって異なります。
   > 
   > 

## <a name="print-a-report-page"></a>レポート ページの印刷
レポートは、一度に 1 ページを印刷できます。

1. 読み取りビューまたは編集ビューでレポートを開きます。
2. 現在のレポート ページを印刷するには、**[ファイル]** > **[印刷]** の順に選択します。
   
    ![Power BI ファイル メニュー](./media/end-user-print/power-bi-print.png)
3. お使いのブラウザーの [印刷] ウィンドウが開きます。
   
   > [!NOTE]
   > 表示される印刷ダイアログ ボックスは、お使いのブラウザーによって異なります。
   > 
   > 

## <a name="print-a-report-visual"></a>レポートのビジュアルの印刷
1. タイルをポイントし、右上隅のフォーカス アイコン ![フォーカス アイコン](./media/end-user-print/power-bi-focus-icon.png) を選ぶことにより、[フォーカス モードでビジュアルを開きます](end-user-focus.md)。
2. 上記の「*レポート ページの印刷*」にある手順 2 ～ 3 に従って操作します。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
* Q:**[印刷]** ボタンが見つかりません。    
* A:Power BI Desktop を使用している場合、印刷はサポートされていません。  印刷は、Power BI サービスでのみ機能します。
* Q:すべてのレポート ページを一度に印刷できません。    
* A:これは正しい動作です。 レポートは、一度に 1 ページのみ印刷できます。
* Q:PDF に出力できません。    
* A:このオプションは、ブラウザーに PDF ドライバーを構成している場合のみ表示されます。    
* Q:**[印刷]** を選択したときに表示される画面が、ここに示されている図と一致しません。    
* A:印刷画面は、ブラウザーとソフトウェアのバージョンによって異なります。
* Q:印刷の拡大縮小が正しく行われません。  ダッシュボードがページに収まりません。 印刷の向きなどに問題があります。    
* A:印刷結果が Power BI サービスでの表示と必ず同じになることは保証できません。 拡大/縮小、余白、ビジュアルの詳細、向き、サイズなどは、Power BI によって制御されません。 このような問題については、お使いのブラウザーのマニュアルを参照してください。      

## <a name="next-steps"></a>次の手順
[同僚や他のユーザーとダッシュボードやレポートを共有する](../service-share-dashboards.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

