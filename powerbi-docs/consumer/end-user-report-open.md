---
title: レポートの表示
description: このトピックによれば、Power BI コンシューマーとエンドユーザーは Power BI レポートを開いて確認する必要がありました。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/04/2018
ms.author: mihart
ms.openlocfilehash: b22da2df92c0cc7130c7a5ebf69e2284c12ffef4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73861969"
---
# <a name="view-a-report-in-the-power-bi-service-for-consumers"></a>*コンシューマー*向け Power BI サービスでレポートを表示する

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

レポートは、ビジュアルで構成される 1 つまたは複数のページです。 レポートは Power BI "*デザイナー*" によって作成され、["*コンシューマー*" と直接](end-user-shared-with-me.md)、または[アプリ](end-user-apps.md)の一部として共有されます。 

レポートはさまざまな方法で開くことができますが、そのうちの [ホーム] から開く方法とダッシュボードから開く方法の 2 つを説明します。 

<!-- add art-->


## <a name="open-a-report-from-power-bi-home"></a>Power BI ホームからレポートを開く
それでは、ユーザーと直接共有されているレポートを開いてみましょう。その後で、アプリの一部として共有されたレポートを開いてみましょう。

   ![ホーム ページ](./media/end-user-report-open/power-bi-home-canvas.png)

### <a name="open-a-report-that-has-been-shared-with-you"></a>ユーザーと共有されているレポートを開く
Power BI "*デザイナー*" では、電子メールのリンクを使用したり、自動的に追加したりすることで、個々のレポートを直接共有できます。 この方法で共有されたコンテンツは、ナビ ペインの **[自分と共有]** コンテナーとホーム キャンバスの **[自分と共有]** セクションに表示されます。

1. Power BI サービス (app.powerbi.com) を開きます。

2. ナビ ペインで、 **[ホーム]** を選択して自分のホーム キャンバスを表示します。  

   ![ホーム キャンバス](./media/end-user-report-open/power-bi-select-home-new.png)
   
3. **[共有アイテム]** が表示されるまで下方向にスクロールします。 レポート アイコン ![レポート アイコン](./media/end-user-report-open/power-bi-report-icon.png) を見つけます。 このスクリーンショットには、1 つのダッシュボードと "*売上およびマーケティングのサンプル*" という名前のレポートが 1 つあります。 
   
   ![ホーム ページの [共有アイテム] セクション](./media/end-user-report-open/power-bi-shared-new.png)

4. レポートを開くには、レポート "*カード*" を選択するだけです。

   ![レポート ページ](./media/end-user-report-open/power-bi-open.png)

5. 左側にタブが並んでいます。  各タブはレポート *ページ*を表します。 現在、"*成長の機会*" ページが開いています。 "*YTD カテゴリ*" タブを選択して、代わりにそのレポート ページを開きます。 

   ![レポート ページ タブ](./media/end-user-report-open/power-bi-ytd.png)

6. 右側に **[フィルター]** ウィンドウが表示されることに注意してください。 このレポート ページまたはレポート全体に適用されているフィルターが、ここに表示されます。

7. レポートのビジュアルの上にカーソルを置くと、いくつかのアイコンと**その他のオプション** (...) が表示されます。特定のビジュアルに適用されているフィルターを確認するには、[フィルター] アイコンを選択します。 ここでは、*Rolling Period および Region による Total Units* の折れ線グラフのフィルター アイコンを選択しています。

   ![レポート ページ タブ](./media/end-user-report-open/power-bi-visual-filters.png)

6. これで、レポート ページ全体が表示されます。 ページの表示 (ズーム) を変更するには、右上隅にある [表示] ドロップダウンを選択し、 **[実際のサイズ]** を選択します。

   ![ズームの変更](./media/end-user-report-open/power-bi-fit-new.png)

   ![ページに合わせる](./media/end-user-report-open/power-bi-actual.png)

### <a name="open-a-report-that-is-part-of-an-app"></a>アプリの一部となっているレポートを開く
仕事仲間や AppSource からアプリを受け取っている場合、そのアプリは [ホーム] とナビ ペインの **[アプリ]** コンテナーから利用できます。 [アプリ](end-user-apps.md)はダッシュボードとレポートをまとめたものです。

### <a name="prerequisites"></a>前提条件
先に進むには、売上およびマーケティング アプリをダウンロードしてください。
1. ブラウザーで、appsource.microsoft.com に移動します。
1. "Sales and Marketing" を検索し、**Microsoft sample - Sales & Marketing** を選択します。
1. **[今すぐ入手する]**  >  **[続行]**  >  **[インストール]** を選択して、アプリ コンテナーにアプリをインストールします。 

アプリ コンテナーまたはホームからアプリを開くことができます。
1. ナビ ペインから **[ホーム]** を選択して、[ホーム] に戻ります。

7. **[マイ アプリ]** が表示されるまで下方向にスクロールします。

   ![ホーム ページ](./media/end-user-report-open/power-bi-app.png)

8. 新しい営業およびマーケティング アプリを選択して開きます。 アプリでは、アプリ *デザイナー*によって設定されたオプションに基づき、ダッシュボードまたはレポートが開きます。 このアプリはダッシュボードに開かれます。  


## <a name="open-a-report-from-a-dashboard"></a>ダッシュボードからレポートを開く
レポートはダッシュボードから開くことができます。 ほとんどのダッシュボード [タイル](end-user-tiles.md)はレポートから "*ピン留め*" されています。 タイルを選択すると、タイルの作成に使用されたレポートが開きます。 

1. ダッシュボードからタイルを選択します。 この例では、"Total Units YTD..." という縦棒グラフ タイルを選択しています。

    ![タイルが選択されているダッシュボード](./media/end-user-report-open/power-bi-dashboard.png)

2.  関連付けられているレポートが開きます。 "YTD Category" ページが表示されていることがわかります。 これは、ダッシュボードから選択した縦棒グラフを含むレポート ページです。

    ![読み取りビューで開かれたレポート](./media/end-user-report-open/power-bi-report-tabs.png)

> [!NOTE]
> 一部のタイルはレポートに関連付けられていません。 [Q&A を使用して作成](end-user-q-and-a.md)されたタイルを選択すると、Q&A 画面が開きます。 [ダッシュボードの **[タイルの追加]** ウィジェットを使用して作成](../service-dashboard-add-widget.md)されたタイルを選択すると、ビデオが再生されたり、Web サイトが開いたりなど、さまざまなことが起こる場合があります。  


##  <a name="still-more-ways-to-open-a-report"></a>レポートを開く他の方法
Power BI サービスのナビゲーションに慣れてくると、最適なワークフローを見つけ出すことができます。 レポートにアクセスする他の方法をいくつか以下に示します。
- ナビ ペインで **[お気に入り]** と **[最近]** を使用する    
- [[関連の表示]](end-user-related.md) を使用する    
- メールで (他のユーザーに[共有してもらう](../service-share-reports.md)場合、または自分で[アラートを設定する](end-user-alerts.md)場合)    
- [通知センター](end-user-notification-center.md)から    
- ワークスペースから
- その他

## <a name="next-steps"></a>次の手順
[ダッシュボードを開いて表示する](end-user-dashboard-open.md)    
[レポートのフィルター](end-user-report-filter.md)

