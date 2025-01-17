---
title: Power BI Desktop から Power BI サービスのデータセットに接続する
description: 複数のワークスペース内の複数の Power BI Desktop レポートに共通のデータセットを使い、レポートのライフサイクルを管理します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d7d48b78ecced3e26a52df12bc8850ab8fed4c1e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877890"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Power BI Desktop から Power BI サービスのデータセットに接続する
Power BI サービスの共有データセットへのライブ接続を確立し、同じデータセットから多数の異なるレポートを作成できます。 つまり、Power BI Desktop で自分の完全なデータ モデルを作成し、それを Power BI サービスに発行することができます。 そうすれば、その同じ共通のデータ モデルから、あなたと他の人は複数のさまざまなレポート (別々の .pbix ファイルに) を作成し、それらを異なるワークスペースに保存できます。 この機能は、**Power BI サービス ライブ接続**と呼ばれます。

![Power BI サービスからデータを取得する](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

この機能にはベスト プラクティスなどあらゆる種類の利点があり、この記事ではそれについて説明します。 考慮事項と制限もいくつかあり、この記事の最後に記載してあるので、よく読んでおいてください。

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>レポートのライフサイクル管理に Power BI サービス ライブ接続を使う
Power BI の 1 つの課題は、レポート、ダッシュボード、およびその基になるデータ モデルの急増です。 このようなことが問題になるのは、**Power BI Desktop** で説得力のあるレポートを簡単に作成し、そのレポートを **Power BI サービス**で共有 ([発行](desktop-upload-desktop-files.md)) して、それらのデータセットから優れたダッシュボードを作成できるためです。 非常に多くのユーザーが、多くの場合は同じ (またはほぼ同じ) データセットを使って、これを行うため、レポートの基になっているデータセットや、各データセットの新しさを把握することが、困難になります。 **Power BI サービス ライブ接続**はそのような課題に対処し、共通のデータセットに基づくレポートとダッシュボードの作成、共有、拡張を、簡単かつ一貫性のあるものにします。

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>誰でも使用できるデータセットを作成して共有する
Anna (ビジネス アナリスト) はチームのメンバーであり、優れたデータ モデル (しばしばデータセットと呼ばれます) を作成する技能があるとします。 Anna は専門知識を駆使してデータセットとレポートを作成し、そのレポートを **Power BI サービス**で共有します。

![Power BI サービスに公開する](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

だれもが Anna のレポートとデータセットを好みますが、それが問題の始まりです。チームの全員がそのデータセットの "*自分用バージョン*" を作成し、自分のレポートをチームで共有しようとします。 そして突然、**Power BI サービス**のチームのワークスペースに、(異なるデータセットに基づく) 大量のレポートが出現します。 どれが最新のものでしょう。 データセットは同じですか、それともほぼ同じなだけですか。 何が違うのですか。 **Power BI サービス ライブ接続**機能を使うと、このようなことをすべて改善できます。 次のセクションでは、Anna が発行したデータセットを、他のユーザーが自分のワークスペース内の自分のレポートに使用し、誰もが、同じ検証され確実な発行済みデータセットを使って独自のレポートを作成できるようにする方法を説明します。

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>ライブ接続を使用して Power BI サービス データセットに接続する
Anna がレポート (および、その基になるデータセット) を作って **Power BI サービス**に発行すると、Power BI サービスのチームのワークスペースに表示されます。 Anna がそれを "*新しいエクスペリエンス ワークスペース*" に保存した場合、Anna は自分のワークスペースの内外にいるすべての人がそれを表示および使用できるように、ビルド アクセス許可を設定することができます。

新しいエクスペリエンス ワークスペースの詳細については、[ワークスペース](service-new-workspaces.md)に関するページを参照してください。

Anna のワークスペースの内外の他のメンバーは、(**Power BI サービス ライブ接続**機能を使って) Anna の共有データ モデルへのライブ接続を確立し、"*それらのメンバーの独自の新しいエクスペリエンス ワークスペース*内" で "*彼らのオリジナルなデータセット*" から独自のレポートを作成することができます。

次の図は、Anna が **Power BI Desktop** レポートを作成し、**Power BI サービス**に (データ モデルを含む) それを発行する様子を示しています。 次に、他のユーザーは、**Power BI サービス ライブ接続**を使って Anna のデータ モデルに接続し、Anna のデータセットを基にして独自のワークスペース内で独自のレポートを作成できます。

![同じデータセットに基づく複数のレポート](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> 自分のデータセットを[従来の共有ワークスペース](service-create-workspaces.md)に保存した場合は、そのデータセットに基づいてレポートを作成できるのはそのワークスペースのメンバーのみとなります。 Power BI サービス ライブ接続を確立するには、接続先のデータセットが共有されているワークスペースのメンバーである必要があります。
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Power BI サービス ライブ接続を使う手順
**Power BI サービス ライブ接続**の有用性と、レポート ライフサイクル管理のベスト プラクティス手法としてそれを使う方法はわかったので、Anna の優れたレポート (およびデータセット) を Power BI チームメートが使用できる共有データセットに発行する手順を見ていきます。

### <a name="publish-a-power-bi-report-and-dataset"></a>Power BI レポートとデータセットを発行する
**Power BI サービス ライブ接続**を使ってレポートのライフサイクルを管理する最初の手順は、チームメートが使いたくなるレポート (とデータセット) を用意することです。 したがって、まず、Anna は **Power BI Desktop** からレポートを**発行**する必要があります。 そうするには、Power BI Desktop の **[ホーム]** リボンで **[発行]** を選択します。

![レポートを発行する](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Anna が Power BI サービス アカウントにサインインしていない場合は、サインインするように求めるポップアップが表示されます。

![Power BI Desktop にサインインする](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

そこで、レポートとデータセットの発行先となるワークスペースを選択できます。 ただし、Anna がそれを新しいエクスペリエンス ワークスペースに保存した場合、ビルド アクセス許可を持つユーザーならだれでもそのデータセットにアクセスできるようになります。 ビルド アクセス許可は、発行後に Power BI サービスに設定されます。 ワークが従来のワークスペースに保存された場合、レポートが発行されるワークスペースにアクセスできるメンバーだけが、**Power BI サービス ライブ接続**を使ってそのデータセットにアクセスすることができます。

![Power BI サービスに公開する](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

発行プロセスが開始し、**Power BI Desktop** に進行状況が表示されます。

![発行が進行中](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

完了すると、**Power BI Desktop** に、成功したことと、**Power BI サービス**内のレポート自体およびレポートの**クイック分析情報**を取得するための 2 つのリンクが表示されます。

![発行に成功](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

データセットを含むレポートが Power BI サービスに発行されたので、それを*昇格*させて、その品質と信頼性を証明することもできます。 さらに、ご利用の Power BI テナント内の中央機関によってそれが "*認定*" されるように要求することもできます。 これらの推奨のいずれかを使用すると、ユーザーがデータセットを探すとき、そのデータセットは常にリストの先頭に表示されます。 関心がある場合は、こちらで、[自分のデータを昇格させる](service-datasets-promote.md)プロセスの詳細を確認できます。 

最後の手順は、レポートの基になっているデータセットに対して*ビルド アクセス許可*を設定することです。 ビルド アクセス許可では、自分のデータセットの表示および使用を誰に許可するかを決定します。 これは、ワークスペース自体に設定することも、ワークスペースからアプリを共有するときに設定することもできます。 ビルド アクセス許可の設定の詳細については、[こちら](service-datasets-build-permissions.md)を参照してください。

次に、レポート (とデータセット) が発行されたワークスペースにアクセスできる他のチームメートが、データセットに接続して独自のレポートを作成する方法を説明します。

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>発行されたデータセットへの Power BI サービス ライブ接続を確立する
発行されたレポートへの接続を確立し、発行されたデータセットを基にして独自のレポートを作るには、**Power BI Desktop** の **[ホーム]** リボンで **[データの取得]** を選び、左側のウィンドウから **[Power BI]** 、 **[Power BI データ セット]** の順に選びます。

Power BI にサインインしていない場合は、サインインするように促されます。 ログインすると、自分がメンバーであるワークスペースを示すウィンドウが表示され、**Power BI サービス ライブ接続**の確立先データセットを含むワークスペースを選ぶことができます。

リスト内のデータセットはすべて、共有されたデータセットであり、これらに対してはどのワークスペースでもビルド アクセス許可が与えられています。 特定のデータセットを検索すれば、その名前および所有者に加えて、それが存在するワークスペース、それが最後に更新された日時を確認できます。 リストの上部には、認定済みまたは昇格済みの*推奨された*データセットも表示されます。 

![使用可能なデータセットの一覧](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

ウィンドウから **[読み込み]** を選ぶと、選んだデータセットへのライブ接続が確立されます。つまり、表示されるデータ (フィールドおよび値) は、リアルタイムで **Power BI Desktop** に読み込まれます。

![[フィールド] ウィンドウ内のデータセット フィールド](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

複数のユーザーが同じデータセットからカスタム レポートを作成して共有できるようになります。 これは、Anna のような有能なユーザーがよくできたデータセットを作成し、他の多くのチームメートは共有データセットを使って独自のレポートを作成できる、優れた方法です。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項
**Power BI サービス ライブ接続**を利用するとき、注意すべきいくつかの制限事項と考慮事項があります。

* 公開されたデータセットに **Power BI サービス ライブ接続**を使って接続できるのは、データセットに対してビルド アクセス許可を持つユーザーだけです。 
* 無料ユーザーに表示されるのは、マイ ワークスペース内のデータセットと Premium ベース ワークスペース内のデータセットのみです。
* これはライブ接続のため、**SQL Server Analysis Services** に接続するときの動作と同様に、左側のナビゲーションおよびモデリングは無効になります。各レポートでは、1 つのデータセットだけに接続できます。
* これはライブ接続のため、**SQL Server Analysis Services** に接続するときと同様に、RLS (行レベルとロールレベルのセキュリティ) や、他のそのような接続動作が適用されます。
* 所有者が元の共有 .pbix ファイルを変更すると、**Power BI サービス**で共有されているデータセットおよびレポートが上書きされます。 そのデータセットに基づくレポートは上書きされませんが、データセットに加えられた変更はいずれもレポートに反映されます。
* ワークスペースのメンバーは、もともと共有されていたレポートを置き換えることはできません。 置き換えようとすると、ファイルの名前を変更して発行するよう求める警告が表示されます。
* **Power BI サービス**で共有データセットを削除した場合、そのデータセットに基づく他のレポートが正常に動作しなくなるか、それらのビジュアルが表示されなくなります。
* コンテンツ パックの場合は、**Power BI サービス**に .pbix レポートおよびデータセットを共有するための基礎として使う前に、コンテンツ パックのコピーを作成しておく必要があります。
* "*自分の所属組織*" からのコンテンツ パックの場合、コピーした後は、サービスで作成されたレポートや、ライブ接続でのコンテンツ パックのコピーの一部として作成されたレポートを、置き換えることはできません。 置き換えようとすると、ファイルの名前を変更して発行するよう求める警告が表示されます。 このような状況では、発行されたライブ接続されているレポートのみを置換できます。
* **Power BI サービス**で共有データセットを削除すると、**Power BI Desktop** からそのデータセットにアクセスできなくなります。
* Power BI サービスでデータセットが共有されるレポートでは、Power BI REST API を使用した自動デプロイはサポートされていません。

