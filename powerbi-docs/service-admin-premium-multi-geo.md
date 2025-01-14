---
title: Power BI Premium の Multi-Geo のサポート
description: Power BI テナントのホーム リージョン以外のリージョンにあるデータセンターにコンテンツを展開する方法について説明します。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 129cef8a923b27582bd6424c8d025b93ecbe5532
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873457"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Power BI Premium の Multi-Geo のサポートを構成する

Multi-Geo は、多国籍企業のお客様が、リージョン、業界固有、または組織のデータの配置場所に関する要件に対応するために役立つ Power BI Premium の機能です。 Power BI Premium をご利用の場合、Power BI テナントのホーム リージョン以外のリージョンにあるデータセンターにコンテンツを展開できます。 geo (地域) には、複数のリージョンが含まれる可能性があります。 たとえば、米国は geo であり、米国中西部と米国中南部は米国のリージョンです。 次のいずれかのリージョンにコンテンツを展開することができます。

- 米国
- カナダ
- イギリス
- ブラジル
- ヨーロッパ
- 日本
- インド
- アジア太平洋
- オーストラリア
- アフリカ

Multi-Geo は、Power BI Germany、21Vianet が運営する Power BI China、または米国政府向け Power BI では使用できません。

Multi-Geo は、Power BI Embedded でも使用できるようになりました。 詳細については、「[Power BI Embedded の Multi-Geo のサポート](developer/embedded-multi-geo.md)」をご覧ください。

## <a name="enable-and-configure"></a>有効化と構成

新しい容量の場合、Multi-Geo を有効にするには、ドロップダウンから既定のリージョン以外のリージョンを選択します。  利用可能な容量ごとに、**米国中西部**など、現在配置されているリージョンが表示されます。

![容量のサイズ: リージョンを選択します。 Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

容量を作成すると、そのリージョン内に残り、作成されるすべてのワークスペースのコンテンツはそのリージョンに保存されます。 ワークスペースの設定画面のドロップダウンから、ワークスペースを別のリージョンに移行することができます。

![ワークスペースの編集:利用可能な容量を選択します。 Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

変更を確認するこのメッセージが表示されます。

![割り当てられたワークスペースの変更の確認](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

移行中のこの時点では、ゲートウェイの資格情報をリセットする必要はありません。  Premium の容量リージョンに保存した後は、移行時にリセットする必要があります。

移行中は、新しいデータセットの発行やスケジュールされたデータの更新など、一部の操作が失敗することがあります。  

Multi-Geo を有効にすると、次の項目は Premium リージョンに格納されます。

- インポートおよび DirectQuery データセットのモデル (.ABF ファイル)
- クエリ キャッシュ
- R イメージ

以下の項目はテナントのホーム リージョン内に残ります。

- プッシュ データセット
- Excel ブック
- ダッシュボード/レポートのメタデータ: タイル名、タイルのクエリなど
- ゲートウェイ クエリまたはスケジュールされた更新ジョブのサービス バス
- アクセス許可
- データセットの資格情報

## <a name="view-capacity-regions"></a>容量のリージョンを表示する

管理ポータルでは、Power BI テナントのすべての容量とその現在のリージョンを確認できます。

![Premium 容量を表示する](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>既存のコンテンツのリージョンを変更する

既存のコンテンツのリージョンを変更する必要がある場合は、2 つの選択肢があります。

- 2 つ目の容量を作成し、ワークスペースを移行します。 無料版をご利用の場合、テナントに予備の仮想コアがある限り、ダウンタイムが発生しません。
- 2 つ目の容量を作成することを選択できない場合、一時的にコンテンツを Premium から共有容量に戻すことができます。 追加の仮想コアは必要ありませんが、無料版をご利用の場合は、ある程度のダウンタイムが発生します。

## <a name="move-content-out-of-multi-geo"></a>Multi-Geo からコンテンツを移行する  

次の 2 つの方法のいずれかで Multi-Geo 容量からワークスペースを取り出すことができます。

- ワークスペースが存在する現在の容量を削除します。  その結果、ワークスペースはホーム リージョンの共有容量に戻されます。
- 個々のワークスペースを、ホーム テナントにある Premium 容量に戻します。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

- データ転送を開始する前に、リージョン間で開始されるすべての動作が、会社と政府のコンプライアンス要件をすべて満たしていることを確認してください。
- リモート リージョンに格納されているキャッシュ クエリは、保存時はそのリージョン内に残ります。 ただし、転送中の他のデータは、複数の地域間を行き来する可能性があります。
- Multi-Geo 環境でデータを別のリージョンに移行する場合、ソース データは、データが移行された元のリージョンに最大 30 日間残る可能性があります。 その間、エンド ユーザーはそのデータにアクセスできません。 30 日の期間中に、そのデータはこのリージョンから削除され、破棄されます。
- 一般的に、Multi-Geo でパフォーマンスが向上することはありません。 レポートとダッシュボードの読み込み処理の場合、ホーム リージョンに対してメタデータを要求する必要があります。
- [データフロー](service-dataflows-overview.md)の機能は、この時点では Multi-GEO でサポートされていません。

## <a name="next-steps"></a>次の手順

- [Power BI Premium とは何ですか?](service-premium-what-is.md)
- [Power BI Embedded の容量に対する Multi-Geo](developer/embedded-multi-geo.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
