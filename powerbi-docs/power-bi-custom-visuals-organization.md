---
title: "Power BI で組織のカスタム ビジュアルを使用する"
description: "Power BI で組織のカスタム ビジュアルを使用、管理、作成する"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: maghan
ms.openlocfilehash: 2c90ea4a7e95c354b6dfaec04cff7e5e4009b55f
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Power BI で組織のカスタム ビジュアルを使用する (プレビュー)

Power BI でカスタム ビジュアルを使用し、独自のビジュアルを作成したり、伝えたいことをデータ インサイトで作成したりできます。 多くの場合、このようなカスタム ビジュアルは開発者が作成します。Power BI にたくさん付属しているビジュアルでは要件を満たさないときに作成されます。 

カスタム ビジュアルが重要視される組織もあります。その組織に特有のデータやインサイトを伝えるために必要だからです。その組織だけのビジネス手法を反映し、データに特別な要件が求められることもあります。 そのような組織はカスタム ビジュアルを開発し、組織全体で共有し、適切に保守管理する必要があります。 Power BI カスタム ビジュアル (現在、プレビュー版) はまさにその機能を組織に与えます。 

次の図は、Power BI における組織のカスタム ビジュアル (プレビュー) のフロー プロセスを示したものです。管理者から始まり、開発と保守管理を経由し、最終的にデータ アナリストの元に届けられます。

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>組織のカスタム ビジュアル (プレビュー) を有効にする方法

組織のカスタム ビジュアルは現在プレビューの段階にあります。そのため、Power BI Desktop でこの機能を有効にする必要があります。 このプレビュー機能を有効にするには、リボンから [ファイル]、[オプションと設定]、[オプション] の順に選択し、左のウィンドウでプレビュー機能を選択し、[組織のカスタム ビジュアル] の横にあるチェックボックスをオンにします。次の画像を参照してください。

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

組織のビジュアルが展開されます。これは Power BI 管理者が管理ポータルから管理します。 組織のリポジトリに展開されると、組織のユーザーは簡単に見つけて、Power BI Desktop から直接、自分のレポートに組織のカスタム ビジュアルをインポートできます。

## <a name="using-organizational-custom-visuals"></a>組織のカスタム ビジュアルを使用する

作成したレポートで組織のカスタム ビジュアルを使用する方法については、組織のカスタム ビジュアルをレポートにインポートする方法を紹介している[この記事](power-bi-custom-visuals.md)を参照してください。
 
## <a name="administering-organizational-custom-visuals"></a>組織のカスタム ビジュアルを管理する

組織のカスタム ビジュアルを管理し、展開する方法については、組織のカスタム ビジュアルの展開と管理について説明している[この記事](https://go.microsoft.com/fwlink/?linkid=866790)を参照してください。

> [!WARNING]
> カスタム ビジュアルには、セキュリティやプライバシーのリスクがあるコードが含まれる場合があります。 組織のリポジトリに展開する前に、カスタム ビジュアルの作成者とソースを信頼できることを確認してください。 
> 

## <a name="considerations-and-limitations"></a>考慮事項と制限事項
 
組織のカスタム ビジュアルはプレビュー段階にあるため、いくつかの事項と制約を考慮する必要があります。
 
管理者:

* レガシ カスタム ビジュアル (新しいバージョンの API に基づいて作成されていないカスタム ビジュアルなど) はサポートされていません。

* インプレース更新はまだサポートされていません。 ビジュアルを更新するには、新しいバージョンのビジュアルを組織のリポジトリにアップロードする必用があります (PBIVIZ ファイルの Visual ID が同じであることも確認してください)。 レポートの作成者がその後、新しいバージョンを自分のレポートにインポートし、レポートで現在のバージョンのビジュアルをインプレース置換できます。

* カスタム ビジュアルがリポジトリから削除されると、削除されたそのビジュアルを利用している既存のレポートでレンダリングが停止します。 リポジトリからの削除は元に戻せません。
 
エンド ユーザー:

* パブリック マーケットプレース (AppSource) と組織のリポジトリから同じビジュアル (同じ Visual ID) を使用することはできません。 インポートされた中で最も新しいビジュアルが使用されます。

* ダッシュボードとレポートでは、組織のビジュアルを外部共有できません。 組織のカスタム ビジュアルが含まれるダッシュボードを組織の外にいるユーザーが見ると、空のビジュアルが表示されます。 

* 組織のビジュアルでは、Power BI ワークスペース コレクションを利用できません。

* Web に公開されているレポートに含まれる組織のカスタム ビジュアルはレンダリングされません。

* AppSource マーケットプレースの Visio ビジュアル、PowerApps ビジュアル、GlobeMap ビジュアルは、組織のリポジトリから展開された場合、レンダリングされません。

* 管理者がリポジトリからカスタム ビジュアルを削除するとき、そのビジュアルがレポートで使用されている場合、そのビジュアルはレンダリングを停止します。レポートを保存するには、レポートから削除する必要があります。