---
title: 'チュートリアル: Power BI サービスでデータ アラートを設定する'
description: このチュートリアルでは、Microsoft Power BI サービスで設定した制限を超えてダッシュボード内のデータが変更された場合に通知されるように、アラートを設定する方法について説明します。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 10/08/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: ba27b42d6449d38fef2659507f035144c67f23fd
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223216"
---
# <a name="tutorial-set-data-alerts-in-power-bi-service"></a>チュートリアル: Power BI サービスでデータ アラートを設定する
アラートを設定すると、ダッシュボード内のデータが設定した制限を超えて変更された場合に通知されます。 

Power BI Pro のライセンスがある場合、または [Premium 容量](../service-premium.md)からダッシュボードを共有されている場合は、タイルにアラートを設定できます。 アラートは、レポートのビジュアルからピン留めされたタイルでのみ、ゲージ、KPI、カードに対してだけ設定できます。 アラートは、レポートからダッシュボードにピン留めしたストリーミング データセットから作成されるビジュアルに設定できますが、**[タイルの追加]** > **[カスタム ストリーミング データ]** でダッシュボードで直接作成したストリーミング タイルには設定できません。 

ダッシュボードを共有している場合であっても、見ることができるのは自分で設定したアラートだけです。 データ アラートはプラットフォーム間で完全に同期されます。[Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)および Power BI サービスで、データ アラートを設定して表示できます。 

![タイル](../media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> データ ドリブン アラート通知は、データに関する情報を提供します。 モバイル デバイスで Power BI データを表示し、そのデバイスが盗まれた場合、Power BI サービスを使用して、すべてのデータ ドリブン アラート ルールをオフにすることをお勧めします。
> 

このチュートリアルでは、以下について説明します。
> [!div class="checklist"]
> * 通知を設定できるユーザー
> * アラートをサポートするビジュアル
> * アラートが表示される対象のユーザー
> * Power BI Desktop およびモバイルでアラートを操作する
> * アラートを作成する方法
> * アラートを受信する場所

Power BI にサインアップしていない場合は、[無料の試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

## <a name="set-data-alerts-in-power-bi-service"></a>Power BI サービスでのデータ アラートの設定
Amanda がダッシュボードのタイルにアラートを追加するところをご覧ください。 その後、ビデオで説明されている手順に従って、ご自分でやってみてください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

この例では、[Retail Analysis サンプル](http://go.microsoft.com/fwlink/?LinkId=529778) ダッシュボードのカード タイルを使用します。

1. ダッシュボードのゲージ、KPI、またはカード タイルで、省略記号を選びます。
   
   ![[Total Stores] タイル](media/end-user-alerts/powerbi-card.png)
2. ベルのアイコン ![アラート アイコン](media/end-user-alerts/power-bi-bell-icon.png)、または **[アラートの管理]** を選択して、**[総店舗数]** に 1 つまたは複数のアラートを追加します。
   
1. **[アラートの管理]** ウィンドウで、**[+ アラート ルールの追加]** を選択します。  スライダーが **[オン]** に設定されていることを確認し、アラートのタイトルを指定します。 タイトルは、アラートの内容を簡単に理解するために役立ちます。
   
   ![アラート管理ウィンドウ](media/end-user-alerts/powerbi-alert-title.png)
4. 下にスクロールして、アラートの詳細を入力します。  この例では、"Total stores" の値が 100 を超えた場合に 1 日に 1 回通知するアラートを作成します。 アラートは通知センターに表示されます。 電子メールの送信も設定します。
   
   ![アラート管理ウィンドウ、しきい値の設定](media/end-user-alerts/power-bi-set-alert-details.png)
5. **[保存して閉じる]** を選びます。

## <a name="receiving-alerts"></a>アラートの受信
追跡対象データがユーザー設定のしきい値のいずれかに達した場合は、いくつかの処理が行われます。 最初に、最後のアラートが送信されてから 1 時間以上または 24 時間以上 (選択したオプションによって異なる) 経過しているかどうかが確認されます。 データがしきい値を超えている場合に限り、アラートを受け取ります。

次に、通知センターにアラートが送信され、さらにオプションで電子メールでもアラートが送信されます。 各アラートにはデータへの直接リンクが含まれています。 リンクを選択して、関連するタイルを表示します。  

1. 電子メールを送信するようにアラートを設定した場合は、次のようなメールを受信します。
   
   ![アラート メール](media/end-user-alerts/powerbi-alerts-email.png)
2. Power BI は、メッセージを**通知センター**に追加し、新しいアラート アイコンを該当するタイルに追加します。
   
   ![Power BI サービスの通知アイコン](media/end-user-alerts/powerbi-alert-notifications.png)
3. アラートの詳細を見るには通知センターを開きます。
   
    ![アラートを読む](media/end-user-alerts/powerbi-alert-notfication.png)
   
   > [!NOTE]
   > アラートは更新されたデータでのみ動作します。 データが更新されると、Power BI はそのデータにアラートが設定されているかどうかを確認します。 データがアラートのしきい値に達した場合、アラートがトリガーされます。
   > 
   > 

## <a name="managing-alerts"></a>アラートの管理
アラートを管理するには多くの方法があります。ダッシュボードのタイル自体、Power BI の [設定] メニュー、[iPhone の Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)または[Windows 10 用の Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)の個別のタイルなどで管理できます。

### <a name="from-the-tile-itself"></a>タイル自体から
1. タイルのアラートを変更または削除する必要がある場合は、ベルのアイコン ![アラート アイコン](media/end-user-alerts/power-bi-bell-icon.png) を選択して **[アラートの管理]** ウィンドウを再び開きます。 そのタイルに設定されているすべてのアラートが表示されます。
   
    ![アラート管理ウィンドウ](media/end-user-alerts/powerbi-see-alerts.png).
2. アラートを変更するには、アラート名の左側にある矢印を選択します。
   
    ![アラート名の横の矢印](media/end-user-alerts/powerbi-see-alerts-arrow.png).
3. アラートを削除するには、アラート名の右側にあるごみ箱を選択します。
   
      ![選択されたごみ箱アイコン](media/end-user-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Power BI の [設定] メニューから
1. Power BI のメニュー バーで歯車アイコンを選択します。
   
    ![歯車アイコン](media/end-user-alerts/powerbi-gear-icon.png).
2. **[設定]** の **[アラート]** を選択します。
   
    ![[設定] ウィンドウの [アラート] タブ](media/end-user-alerts/powerbi-alert-settings.png)
3. ここからは、アラートをオンまたはオフにしたり、**[アラートの管理]** ウィンドウを開いて変更を行ったり、アラートを削除したりできます。

## <a name="tips-and-troubleshooting"></a>ヒントとトラブルシューティング
* 現在、Bing タイルまたは日付/時刻メジャーを含むカード タイルについては、アラートはサポートされていません。
* アラートは、数値データ型でのみ機能します。
* アラートは更新されたデータでのみ動作します。 静的データでは動作しません。
* KPI/カード/ゲージ レポート ビジュアルを作成し、そのビジュアルをダッシュボードにピン留めした場合、アラートはストリーミング データセットでのみ動作します。

## <a name="clean-up-resources"></a>リソースをクリーンアップする
アラートを削除する手順については、上記で説明しています。 手短に言えば、Power BI のメニュー バーで歯車アイコンを選択します。 **[設定]** で **[アラート]** を選択し、アラートを削除します。

> [!div class="nextstepaction"]
> [モバイル デバイスでデータ アラートを設定する](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


