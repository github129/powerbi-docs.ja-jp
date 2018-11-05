---
title: Power BI で Alpine Metrics Sales Predictions に接続する
description: Power BI 用 Alpine Metrics Sales Predictions
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 7bab3839b5f47448a6882d0ea15bb0f253ceb5ea
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46547881"
---
# <a name="connect-to-alpine-metrics-sales-predictions-with-power-bi"></a>Power BI で Alpine Metrics Sales Predictions に接続する
Alpine Metrics は、さまざまな規模の販売組織が利用できる、最新の予測販売プロセス最適化をクラウドやオンデマンドで提供します。 Power BI 用 Alpine Metrics Sales Predictions コンテンツ パックには、売上予測や潜在的リスクなどのメトリックが含まれています。これらのメトリックを使用して、ビジネスの将来に関する深い洞察を得ることができます。 

Power BI 用 [Alpine Metrics Sales Predictions コンテンツ パック](https://app.powerbi.com/getdata/services/alpine-metrics)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある [データの取得] を選択します。  
   
    ![](media/service-connect-to-alpine-metrics/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。  
   
    ![](media/service-connect-to-alpine-metrics/services.png)
3. **[AlpineMetrics Sales Predictions]** を選択した後、**[取得]** を選択します。  
   
    ![](media/service-connect-to-alpine-metrics/alpine.png)
4. **[OAuth 2]** を選択し、**[サインイン]** をクリックします。 要求されたら、AlpineMetrics 資格情報を入力します。
   
    ![](media/service-connect-to-alpine-metrics/creds.png)
   
    ![](media/service-connect-to-alpine-metrics/creds2.png)
5. 接続されると、ダッシュボード、レポート、およびデータセットが自動的に読み込まれます。 完了すると、タイルがユーザーのアカウントのデータで更新されます。
   
    ![](media/service-connect-to-alpine-metrics/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
コンテンツ パックには、次のテーブルのデータが含まれています。  

    - Account    
    - ビジネス    
    - 国    
    - 業界    
    - 営業案件  
    - 人  
    - 予測    
    - 予測履歴    
    - Product  
    - 地域    

## <a name="system-requirements"></a>システム要件
このコンテンツ パックをインスタンス化するには、上記のテーブルへのアクセス許可を持つ Alpine Metrics アカウントが必要です。

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[Power BI - 基本的な概念](consumer/end-user-basic-concepts.md)

