---
title: ホワイトリスト登録用の Power BI の URL
description: この記事では、顧客が Power BI を使用して到達できる必要があるエンドポイントについて説明します。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.custom: seodec18
ms.openlocfilehash: 2771329aef1fe7258065c42269060dc1b9e50bd0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860624"
---
# <a name="power-bi-urls-for-whitelisting"></a>ホワイトリスト登録用の Power BI の URL

**Power BI のオンライン サービス** (Power BI の SaaS (サービスとしてのソフトウェア) アプリケーションとも呼ばれます) には、インターネットへの接続が必要です。 顧客が Power BI のオンライン サービスを使用して到達できる必要があるエンドポイントは、次のとおりです。

Power BI のオンライン サービスを使用するには、次の表で**必須**とマークされているエンドポイントと、リンク先のサイトで**必須**とマークされているすべてのエンドポイントに接続するためのアクセス権が必要です。 外部サイトへのリンクが特定のセクションを参照している場合は、そのセクション内のエンドポイントを確認するだけでかまいません。

**オプション**とマークされているエンドポイントも、特定の機能が動作するために**ホワイト リストに登録**されている場合があります。

Power BI のオンライン サービスで必要なことは、リストに記載されているエンドポイントのために TCP ポート 443 を開いておくことだけです。

ワイルドカード (*) は、ルート ドメインの下のすべてのレベルを表し、情報を利用できない場合には "該当なし" としています。 **ターゲット**列は、FQDN/ドメインと、追加のエンドポイント情報を含む外部サイトへのリンクの一覧です。

>[!Important]
>次の表の情報は、**U. S.Government クラウド**、**Germany クラウド**、または **China クラウド** を表しません。

## <a name="authentication"></a>認証

Power BI は、Office 365 の認証セクションと ID セクションの必須エンドポイントに依存します。 Power BI を使用するには、以下のリンク先のサイト内のエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** 認証と ID | [Office Online および共通の URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) については、Office 365 ドキュメントを参照  | 該当なし |

## <a name="general-site-usage"></a>一般的なサイトの使用

Power BI の一般的な使用では、次の表内とリンク先のサイトのエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** バックエンド API | *.analysis.windows.net | TCP 443 |
| 2 | **必須:** Office 365 の統合 | [Office Online および共通の URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) については、Office 365 ドキュメントを参照 | 該当なし |
| 3 | **必須:** ポータル | app.powerbi.com | TCP 443 |
| 4 | **必須:** サービスの利用統計情報 | dc.services.visualstudio.com | TCP 443 |
| 5 | **オプション:** 情報メッセージ | dynmsg.modpim.com | TCP 443 |
| 6 | **オプション:** NPS 調査 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>管理

Power BI 内で管理機能を実行するには、以下のリンク先のサイト内のエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** ユーザーの管理と監査ログの表示用 | [Office Online および共通の URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) については、Office 365 ドキュメントを参照 | 該当なし |
| | | |

## <a name="getting-data"></a>データの取得

OneDrive などの特定のデータ ソースからデータを取得するには、次の表内のエンドポイントに接続できる必要があります。 組織内で使用されている特定のデータ ソースでは、追加のインターネット ドメインおよび URL へのアクセスが必要となる場合があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** AppSource (Power BI の内部または外部のアプリ) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **オプション:** サインインしてコンテンツ パックのデータを取得する | 使用しているコンテンツパックによって異なる | 使用しているコンテンツパックによって異なる |
| 3 | **オプション:** 個人用 OneDrive からのファイルのインポート | 「[Required URLs and ports for OneDrive](https://docs.microsoft.com/onedrive/required-urls-and-ports)」 (OneDrive に必要な URL とポート) を参照 | 該当なし |
| 4 | **オプション:** Power BI の 60 秒間のチュートリアル ビデオ | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **オプション:** PubNub ストリーミング データ ソース | [PubNub のドキュメント](https://support.pubnub.com/support/solutions/articles/14000043522)を参照 | 該当なし |
| | | |

## <a name="dashboard-and-report-integration"></a>ダッシュボードとレポートの統合

Power BI は、ダッシュボードとレポートをサポートするため、特定のエンドポイントに依存します。 次の表内とリンク先のサイトのエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** Excel との連携 | [Office Online および共通の URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) については、Office 365 ドキュメントを参照 | 該当なし |
| | | |

## <a name="custom-visuals"></a>カスタム ビジュアル

Power BI は、カスタム ビジュアルを表示してアクセスするために、特定のエンドポイントに依存します。 次の表内とリンク先のサイトのエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** Marketplace インターフェイスまたはファイルからカスタム ビジュアルをインポートする | *.azureedge.net <br> *.blob.core.windows.net <br> store.office.com | TCP 443 |
| 2 | **オプション:** Bing マップ | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **オプション:** PowerApps | PowerApps のシステム要件のサイトの「[必要なサービス](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services)」セクションを参照 | 該当なし |
| 4 | **オプション:** Visio | [Office Online および共通の URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)、[SharePoint Online と OneDrive for Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) に関する Office 365 ドキュメントを参照 | 該当なし |
| | | |

## <a name="related-external-sites"></a>関連する外部サイト

その他の関連サイトへの Power BI リンク。 これらのサイトには、ドキュメント、サポート、新しい機能の要望などのサイトが含まれます。 これらのサイトは、Power BI の機能に影響を与えないので、必要に応じてホワイト リストに登録できます。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **オプション:** コミュニティ サイト | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **オプション:** ドキュメントのサイト | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **オプション:** ダウンロード サイト (Power BI Desktop など) | download.microsoft.com | TCP 443 |
| 4 | **オプション:** 外部リダイレクト | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **オプション:** アイデアのフィードバック サイト| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **オプション:** Power BI サイト - ランディング ページ、詳細情報のリンク、サポート サイト、ダウンロード リンク、パートナー ショーケースなど | powerbi.microsoft.com | TCP 443 |
| 7 | **オプション:** Power BI デベロッパー センター | dev.powerbi.com | TCP 443 |
| 8 | **オプション:** サポート サイト | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |