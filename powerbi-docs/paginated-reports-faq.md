---
title: Power BI のページ分割されたレポート:よく寄せられる質問
description: この記事では、ページ分割されたレポートについてよく寄せられる質問に答えます。 これらのレポートは、印刷や PDF 生成用に最適化されている、高度に書式設定されたピクセル単位で完璧な出力です。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 10/04/2019
ms.openlocfilehash: d8fd8490bda3be4217440a984e8b6da6fca7c5cf
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874798"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Power BI のページ分割されたレポート:よく寄せられる質問 

この記事では、ページ分割されたレポートについてよく寄せられる質問に答えます。 これらのレポートは、印刷や PDF 生成用に最適化されている、高度に書式設定されたピクセル単位で完璧な出力です。 これらは、複数のページにちょうど収まるように設定されているため "ページ分割された" と呼ばれます。 ページ分割されたレポートは、SQL Server Reporting Services の RDL レポート テクノロジに基づいています。 

この記事では、Power BI Premium でのページ分割されたレポート、およびページ分割されたレポートを作成するためのスタンドアロン ツールであるレポート ビルダーに関する多くの一般的な質問に回答します。 サービスにレポートを発行するには、Power BI Pro ライセンスが必要です。 ワークスペースが Power BI Premium 容量に存在する限り、マイ ワークスペースまたはワークスペースにページ分割されたレポートを発行して共有できます。 

## <a name="administration"></a>管理

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>ページ分割されたレポートに必要な Premium 容量のサイズはどれくらいですか。

ページ分割されたレポート ワークロードは P1 ～ P3 SKU で利用できます。  A4 から A6 SKU では、埋め込みまたはテスト/開発シナリオに使用することもできます。

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>容量でページ分割されたレポートに対して設定できる最大メモリしきい値はどれくらいですか。

このワークロードに対して最大でメモリの 100% を使用することができます。

### <a name="how-does-user-access-work-for-paginated-reports"></a>ユーザー アクセスはページ分割されたレポートに対してどのように動作しますか。

ページ分割されたレポートに対するユーザー アクセスは、Power BI サービスでの他のすべてのコンテンツに対するユーザー アクセスと同じです。 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>ページ分割されたレポート ワークロードはどのようにしてオン/オフできますか。

容量管理者は、容量管理ポータル ページでページ分割されたレポート ワークロードを有効または無効にできます。  既定では、ワークロードは作成するすべての新しい容量に対して有効になります。  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>テナントでのページ分割されたレポートの利用状況はどのようにして監視できますか。

Office 365 の監査では、次のイベントでこのレポートの種類の詳細な使用状況が記録されます。 

- Power BI レポートの表示
- Power BI レポートの削除
- Power BI レポートの作成
- Power BI レポートのダウンロード

Power BI レポートとページ分割されたレポートを区別するため、ReportType フィールドには "PaginatedReport" という値が設定されます。

また、監査ログでは、ページ分割されたレポートに対して次のイベントが提供されます。

- ゲートウェイに対するバインドされた Power BI データセット
- Power BI データソースの検出
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Premium 容量監視アプリを使ってこのワークロードを監視できますか。

はい。Power BI データセットと同じ関連詳細が含まれる新しいタブで監視できます。

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>ページ分割されたレポートを作成して発行するには、Pro ライセンスが必要ですか。

Pro ライセンスがなくても、お使いのマイ ワークスペースが Premium 容量にあれば、ページ分割されたレポートをそのワークスペースにアップロードできます。  他のワークスペースの場合、コンテンツをそのワークスペースに作成および公開するには Pro ライセンスが必要です。 Pro ライセンスがなくても Power BI レポート ビルダーをダウンロードして使用することをお勧めします。ただし、Pro ライセンスなしでページ分割されたレポートを作成する場合、そのレポートを公開することはできません。 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>ワークスペースにページ分割されたレポートがある状態で、ページ分割されたレポート ワークロードをオフにするとどうなりますか。

エラー メッセージが表示され、ワークロードをオンに戻すまでレポートを表示することはできません。 それでも、ワークスペースからレポートを削除することはできます。

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>ページ分割されたレポートに対してサポートされる各 Premium SKU の既定のメモリは何ですか。

ページ分割されたレポートに対する各 Premium SKU の既定のメモリは次のとおりです。

- **P1/A4**:20% (既定値)、10% (最小値)
- **P2/A5**:20% (既定値)、5% (最小値)
- **P3/A6**:20% (既定値)、2.5% (最小値)

## <a name="general"></a>全般

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>ページ分割されたレポートと Power BI レポートはそれぞれどのようなときに使用する必要がありますか。

ページ分割されたレポートは、印刷や PDF 生成用に最適化されている、高度に書式設定されたピクセル単位で完璧な出力が必要なシナリオに最適です。  損益計算書は、ページ分割されたレポートとして作成するのがおそらく望ましいレポートの種類のよい例です。  

Power BI レポートは、探索と対話性に最適化されています。  異なる営業担当者が、同じレポートのデータを特定の地域/業界/顧客でスライスして業績の変化を見る売上レポートは、Power BI レポートで提供するのが最善です。

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>ドキュメントでは、Power BI レポート ビルダーが推奨される作成ツールになっています。 Power BI 用の SQL Server Data Tools でページ分割されたれたレポートを作成できますか。

はい。ただし、Power BI サービスでは一度に 1 つの項目しかアップロードできないので、作成者が SQL Server Data Tools (SSDT) で使用する多くのシナリオは、まだサポートされていません。 [サポートされていない機能の完全な一覧](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)は、この FAQ で後ほど示します。  

### <a name="what-versions-of-report-builder-do-you-support"></a>どのバージョンのレポート ビルダーがサポートされていますか。

Microsoft では最近 Power BI レポート ビルダーを、ページ分割されたレポート用の主要作成ツールとして Power BI サービスでリリースしました。 [Power BI レポート ビルダーは、Microsoft ダウンロード センターから](https://go.microsoft.com/fwlink/?linkid=2086513)インストールしてください。

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>SQL Server Reporting Services に保存してある既存のレポートを Power BI に移動するにはどうすればよいですか。

サーバーからレポートをダウンロードした後、ポータルを使用して Power BI にアップロードする必要があります。  現時点では使用可能な移行ツールはありませんが、パブリック プレビューが完了し、製品間の機能パリティが適切なレベルになった後で、ツールを作成する予定です。

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>レポートを開いて、サービスに直接発行できますか。

はい。 Microsoft では最近、Power BI レポート ビルダーでレポートを開いて、サービスに直接公開する機能を追加しました。

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>SSRS でのページ分割されたレポートの機能のうち、Power BI でまだサポートされていないものは何ですか。

現在、ページ分割されたレポートでは次のものがサポートされていません。

- 共有データ ソース
- 共有データセット
- サブレポート
- 他のレポートへのドリルスルーとクリックスルー
- リンク レポート
- Bing マップ レイヤー
- カスタム フォント

切り替え/並べ替え以外の Power BI サービスでサポートされていない機能を含むファイルをアップロードしようとすると、エラー メッセージが表示されます。

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>ページ分割されたレポートに対して現在サポートされているデータ ソースは何ですか。

サポートされているデータ ソースは次のとおりです。 

- Power BI データセット (シングル サインオン (SSO) を使用)
- Azure Analysis Services (シングル サインオン (SSO) および oAuth を使用)
- Azure SQL Data Warehouse
- Azure SQL Database (ユーザー名/パスワード、SSO、OAuth)
- パブリック エンドポイント経由の Azure SQL Managed Instance (ユーザー名/パスワード)
- SQL Server*
- SQL Server Analysis Services (SSAS) 表形式 (DAX) および多次元 (MDX) モデル* 
- Oracle* 
- Teradata* 

* オンプレミスのゲートウェイが必要。

ゲートウェイを介した SSAS へのアクセスが機能するには、資格情報が格納されているユーザーに管理者特権のアクセス許可が必要です。

### <a name="what-authentication-methods-do-you-support"></a>どのような認証方法がサポートされていますか。

Azure Analysis Services、Azure SQL Database、Power BI の各データ ソースに対する SSO がサポートされています。  また、Azure SQL Database と Azure Analysis Services に対する OAuth もサポートされています。  他のデータ ソースについては、現在、ポータルまたはゲートウェイでデータ ソースと共にユーザー名とパスワードを格納する必要があります。  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>ページ分割されたレポートのデータ ソースとして、Power BI データセットを使用できますか。

はい。Power BI データセットは、ページ分割されたレポートのデータ ソースとしてサポートされています。

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>ゲートウェイを介してストアド プロシージャを使用できますか。

ゲートウェイ経由でストアド プロシージャを使用できますが、ストアド プロシージャにパラメーターが指定されている場合、特定のシナリオで問題が発生することがあります。

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Power BI サービスでレポートにはどのようなエクスポート形式を使用できますか。

Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、.CSV、XML、MHTML にエクスポートできます。

### <a name="can-i-print-paginated-reports"></a>ページ分割されたレポートを印刷できますか。

はい。ページ分割されたレポートは印刷できます。印刷プレビュー機能が新しくなり、改善されています。 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>ページ分割されたレポートでメール サブスクリプションを使用できますか。

はい。メール サブスクリプションは、ページ分割されたレポートに対して完全にサポートされ、これには 6 つ異なるファイル形式とパラメーター値のサポートが含まれます。

### <a name="can-i-run-custom-code-in-my-report"></a>レポートでカスタム コードを実行できますか。

はい、SSRS と同様に、レポートでもコードを実行する機能がサポートされています。

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Power BI Embedded を使用して、自分がホストしているアプリにページ分割されたレポートを埋め込むことはできますか。

SaaS 埋め込み (Secure Embed のサポートを含む) は既に利用できます。  PaaS 埋め込みは、年内のサポートを予定しています。

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Power BI レポートからページ分割されたレポートにドリルスルーできますか。

はい。ページ分割されたレポートで URL パラメーターを使用して、これを実現することができます。

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Power BI アプリを使って、ページ分割されたレポートの内容を共有できますか。

はい。ページ分割されたレポートは、v1 と v2 の両方のワークスペースのアプリでデプロイされるようにサポートされています。 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>ダッシュボードへのレポート タイルのピン留めのような Power BI での他のレポート固有機能は、ページ分割されたレポートで動作しますか。

可能な限り、サービスと同じ主要シナリオをレポートでもサポートする予定です。  作成ツールは異なっても、利用者の観点からはポータルのリストの他のレポートと同じであることが理想的です。 作成された方法を気にすることなく、必要なことを実現できます。  この機能パリティのよい例は、計画されているコメントのサポートです。 機能自体の動作は各レポートの種類で若干異なる場合がありますが、どちらでもコメントを使用することができます。

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>SSRS の顧客が Power BI に既存のレポートと資産を移動できる移行ツールは計画されていますか。

現在 GitHub のプロジェクトが、SQL Server Reporting Services から Power BI へのコンテンツの移行に対応しています。  こちら ([https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)) でツールの詳細を確認し、ダウンロードしてください。

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Power BI サービスにはページ分割されたレポート用のレポート ビューアー コントロールがありますか。

いいえ、現在は使用できるレポート ビューアー コントロールはありません。

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Power BI サービスの新しいホーム エクスペリエンスからページ分割されたレポートを検索できますか。

はい。ホームから、ページ分割されたレポートを検索できるようになりました。  新しいホーム エクスペリエンスの他の部分にも表示されます。

## <a name="next-steps"></a>次の手順

- [Microsoft ダウンロード センターから Power BI レポート ビルダーをインストールする](https://go.microsoft.com/fwlink/?linkid=2086513)
- [チュートリアル:ページ分割されたレポートを作成する](paginated-reports-quickstart-aw.md)
