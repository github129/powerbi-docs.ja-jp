---
title: Power BI サービスのレポートの読み取りビューと編集ビュー
description: Power BI サービスのレポートの読み取りビューと編集ビューの違いの概要について説明します
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: f108ab3c924f6ff69bc6ee6aae5ed0539ce3f11d
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "48908083"
---
# <a name="reading-view-and-editing-view-in-power-bi-service-reports"></a>Power BI サービスのレポートの読み取りビューと編集ビュー
Power BI サービスには、レポートを表示および操作するためのモードとして、読み取りビューと編集ビューの 2 つがあります (Power BI Desktop にはありません)。 読み取りビューはすべてのユーザーが利用でき、特にデータの*コンシューマー*向けに設計されていますが、編集ビューはレポートの*作成者*と所有者のみが利用できます。

![レポート作成者とレポート コンシューマーのアートワーク](./media/end-user-reading-view/power-bi-creators-consumers.png)

## <a name="report-reading-view"></a>レポートの読み取りビュー

 読み取りビューではレポートを探索し、レポートと対話することができます。楽しく安全に、データについてさまざまなことを試したりよく理解したりすることができます。 読み取りビューは、アプリからレポートを開くユーザーや、レポートを[他のユーザーと共有](../service-share-dashboards.md)しているユーザーなど、レポートの*コンシューマー*向けに設計されています。 読み取りビューでは、特定のレポートのすべてのコンシューマーに対して、同じ視覚エフェクトを含む、(必要に応じて同じフィルターが適用された) 同じレポートが表示されます。  コンシューマーはレポートと対話したり、既存のフィルターを変更したりできますが (その変更内容はレポートと共に保存されます)、新しいフィルターを追加することはできません。

> [!NOTE]
> 行レベルのセキュリティとデータ アクセス許可のため、特定の状況では、レポートのコンシューマーによってデータの表示が異なる場合があります。

## <a name="report-editing-view"></a>レポートの編集ビュー

編集ビューは、レポートの作成者、または[アプリ ワークスペースのメンバーまたは管理者であるレポートの共同所有](../service-create-distribute-apps.md)者のみが使用できます。

編集ビューはレポートの*作成者*向けに設計されています。 ここでは、作成者がデータセットのインポートや接続、データの探索、レポートとダッシュボードのビルドを行います。 編集ビューでは、*作成者*はデータをより詳しく調査できます。その場合、フィールドを追加/削除したり、視覚エフェクトの種類を変更したり、視覚エフェクトを新規作成したり、レポートから視覚エフェクトやページを追加/削除したりします。 その後、作成したレポートを同僚と共有することができます。

## <a name="reading-view-versus-editing-view"></a>読み取りビューと編集ビュー
このグラフには、Power BI サービスのすべてのレポート機能がリストされているわけではありません。 読み取りビューと編集ビューの**両方**では使用できないレポート タスクのみがリストされています。


|タスク  | 読み取りビュー  | 編集ビュー |
|-------------------------|-------|-------|
|**レポート (全体として)**  |
| [レポートの作成または編集](../service-report-create-new.md) | いいえ  | はい |
| [レポートの共有](../service-share-reports.md)| はい | はい。他のユーザーへの*所有者*アクセス許可の付与など、アクセス許可を管理することもできます。 |
| [フィルター ウィンドウからの永続的な (固定) ビジュアル レベル、ドリルスルー、ページ レベル、レポート レベルのフィルターの作成](../power-bi-report-add-filter.md) | いいえ  | はい |
| [レポートのフィルター ウィンドウの使用](end-user-report-filter.md) | はい。既存のフィルターを使用でき、変更内容をレポートと共に保存できますが、新しいフィルターを追加することはできません。 | はい |
| [レポートの分析ウィンドウの使用](../service-analytics-pane.md) | いいえ | はい |
| [レポートの**表示**オプション](../power-bi-report-display-settings.md) | はい。ただし、例外がいくつかあります。 | はい、グリッド線、スナップ、ロックを含むすべてを使用できます。 |
| [更新スケジュールの作成](../refresh-data.md) | いいえ  | はい |
| [レポートへのサブスクライブ](end-user-subscribe.md) | はい | いいえ |
| [Q&A - レポートでの質問](end-user-q-and-a.md) | いいえ  | はい |
| [利用状況指標の表示](../service-usage-metrics.md) | はい、レポート キャンバスで表示できます。 | はい、レポート リスト (コンテンツ ビュー) に表示できます。 |
| [関連の表示](end-user-related.md) | はい、レポート キャンバスで表示できます。 | はい、レポート リスト (コンテンツ ビュー) に表示できます。 |
| [レポートの保存](../service-report-save.md) | はい。ただし、**[名前を付けて保存]** を使用する場合に限ります。 | はい |
| [レポートの削除](../service-delete.md) | いいえ  | はい |
|**レポート ページ** |
| [レポート ページの追加または名前変更](../power-bi-report-add-page.md)  | いいえ  | はい  |
| [レポート ページの複製](../power-bi-report-copy-paste-page.md) | いいえ  | はい |
| [レポート ページの削除](../service-delete.md) | いいえ | はい |
|**レポートの視覚エフェクトの操作**|
| [レポートへの視覚エフェクトの追加](../visuals/power-bi-report-add-visualizations-i.md) | いいえ  | はい |
| [レポートへのテキスト ボックスと図形の追加](../power-bi-reports-add-text-and-shapes.md) | いいえ  | はい |
| [レポートの書式設定ウィンドウの使用](../service-the-report-editor-take-a-tour.md) | いいえ | はい |
| [ビジュアル対話の設定](end-user-interactions.md) | いいえ  | はい |
| [視覚エフェクトの作成に使用されたデータの表示](end-user-show-data.md) | いいえ  | はい |
| [ドリルダウンの構成](end-user-drill.md) | いいえ  | はい |
| [使用中の視覚エフェクトの変更](../visuals/power-bi-report-change-visualization-type.md) | いいえ | はい|
| [視覚エフェクト、テキスト ボックス、または図形の削除](../service-delete.md)| いいえ | はい |


## <a name="navigating-between-editing-view-and-reading-view"></a>編集ビューと読み取りビューの間の移動
編集ビューでレポートを開くことができるのはレポートの作成者と所有者 (複数可) のみであることに注意してください。

1. 通常、既定ではレポートは読み取りビューで開かれます。 **[レポートの編集]** オプションが表示されていれば、読み取りビューで開いていることになります。 **[レポートの編集]** が淡色表示の場合は、レポートを編集ビューで開くアクセス許可がありません。

   ![単色表示の [レポートの編集]](./media/end-user-reading-view/power-bi-edit-report-grey.png)

2. **[レポートの編集]** が淡色表示になっていない場合は、それを選ぶとレポートが編集ビューで開きます。

   ![[レポートの編集] オプション](./media/end-user-reading-view/power-bi-edit-report.png)

   これでレポートが編集ビューに切り替わり、読み取りビューで最後に使用したものと同じ[表示設定](../power-bi-report-display-settings.md)が使用されます。

2. 読み取りビューに戻るには、上部のナビゲーション バーにある **[読み取りビュー]** を選びます。

    ![[読み取りビュー] オプション](./media/end-user-reading-view/power-bi-reading-view.png)



## <a name="next-steps"></a>次の手順
読み取りビューにはレポートを編集するさまざまな手段があり、データを細かく切り分けて洞察を発見し、質問に対する回答を得ることができます。  次のトピックの「[Power BI の読み取りビューでレポートと対話する](../service-interact-with-a-report-in-editing-view.md)」では、これらのいくつかについて詳しく説明されています。    
「[Power BI のレポート](end-user-reports.md)」に戻る    
