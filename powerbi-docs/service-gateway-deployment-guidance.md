---
title: Power BI のデータ ゲートウェイを展開するためのガイダンス
description: Power BI のゲートウェイの展開に関するベスト プラクティスと考慮事項について説明します。
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: d4a02ccc759f78a4243f34fb59115fb9084ea90d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881693"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Power BI のデータ ゲートウェイを展開するためのガイダンス

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

この記事では、ネットワーク環境に Power BI 用にデータ ゲートウェイを展開するためのガイダンスと考慮事項について説明します。

オンプレミス データ ゲートウェイをダウンロード、インストール、構成、および管理する方法の詳細については、「[オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)」を参照してください。 また、オンプレミス データ ゲートウェイと Power BI の詳細については、[Microsoft Power ブログ](https://powerbi.microsoft.com/blog/)と [Microsoft Power BI コミュニティ サイト](https://community.powerbi.com/)を参照してください。

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイのインストールに関する注意点

Power BI クラウド サービス用にオンプレミス データ ゲートウェイをインストールする前に、注意すべきいくつかの考慮事項があります。 以下のセクションでは、これらの考慮事項について説明します。

### <a name="number-of-users"></a>ユーザー数

ゲートウェイを使用するレポートを使用するユーザーの数は、ゲートウェイをインストールする場所を決定するときの重要なメトリックです。 考慮すべきいくつかの質問を次に示します。

* ユーザーは、1 日のうち異なる時間帯にこれらのレポートを使用していますか。
* どのような種類の接続 (DirectQuery またはインポート) を使用していますか。
* すべてのユーザーが同じレポートを使用しますか。

すべてのユーザーが毎日同時に特定のレポートにアクセスする場合は、これらの要求をすべて処理できるコンピューターにゲートウェイをインストールしてください。 コンピューターが適切かどうかを判断するのに役立つパフォーマンスカウンターと最小要件については、以降のセクションを参照してください。

Power BI の制約では、"*レポート*" ごとに "*1 つ*" のゲートウェイのみが許可されます。 レポートが複数のデータ ソースに基づいている場合でも、このようなデータ ソースはすべて 1 つのゲートウェイを経由する必要があります。 ダッシュボードが "*複数*" のレポートに基づいている場合は、関係しているレポートごとに専用のゲートウェイを使用できます。 このようにして、1 つのダッシュボードに関係している複数のレポート間でゲートウェイの負荷を分散します。

### <a name="connection-type"></a>接続の種類

Power BI では、次の 2 種類の接続が提供されます。DirectQuery とインポート。 すべてのデータ ソースが両方の種類の接続をサポートしているわけではありません。 セキュリティ要件、パフォーマンス、データの上限、データ モデルのサイズなどの多くの要因が、どちらを選択するかを判断するのに役立ちます。 接続の種類とサポートされているデータ ソースの詳細については、[使用可能なデータ ソースの種類の一覧](service-gateway-data-sources.md#list-of-available-data-source-types)を参照してください。

使用する接続の種類によっては、ゲートウェイの使用量が異なる場合があります。 たとえば、DirectQuery データ ソースは、スケジュールされた更新データ ソースから可能な限り分離するようにします。 これらは異なるレポートに含まれていて、分離できることを前提としています。 ソースを分離することで、朝にスケジュールされている会社のメイン ダッシュボードで使用される大きなサイズのデータ モデルの更新と同時に、ゲートウェイで数千の DirectQuery 要求がキューに入れられるのを防ぎます。 

各オプションについての考慮事項を次に示します。

* **スケジュールされた更新**:クエリのサイズと、1 日あたりに発生する更新の数に応じて、推奨される最小ハードウェア要件を維持するか、より高いパフォーマンスのコンピューターにアップグレードするかを選択できます。 特定のクエリが折りたたまれていない場合、変換はゲートウェイ コンピューターで行われます。 その結果、より多くの RAM が使用できることでゲートウェイ コンピューターにメリットがもたらされます。

* **DirectQuery**:いずれかのユーザーがレポートを開くかデータを参照するたびにクエリが送信されます。 1,000 を超えるユーザーが同時にデータにアクセスすることを想定している場合は、コンピューターに堅牢で対応可能なハードウェア コンポーネントが備えられていることを確認してください。 CPU コアを増やすと、DirectQuery 接続のスループットが向上します。

コンピューターのインストール要件については、オンプレミス データ ゲートウェイの[インストール要件](/data-integration/gateway/service-gateway-install#requirements)を参照してください。

### <a name="location"></a>場所

ゲートウェイのインストール場所は、クエリのパフォーマンスに大きな影響を与える場合があります。 ネットワークの待機時間を最小限に抑えるために、ゲートウェイ、データ ソースの場所、および Power BI テナントが、互いにできるだけ近い場所にあることを確認します。 Power BI テナントの場所を確認するには、Power BI サービスで、右上にある **[?]**  アイコンを選択します。 次に、**[Power BI について]** を選択します。

![Power BI テナントの場所を決定する](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Azure Analysis Services と共に Power BI ゲートウェイを使用する場合は、両方のデータ領域が一致していることを確認してください。 複数のサービスのデータ領域を設定する方法の詳細については、[こちらのビデオ](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/)をご覧ください。

## <a name="next-steps"></a>次の手順

* [プロキシ設定の構成](/data-integration/gateway/service-gateway-proxy)  
* [ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)  
* [オンプレミス データ ゲートウェイに関するよく寄せられる質問 (FAQ) - Power BI](service-gateway-power-bi-faq.md)  

他にわからないことがある場合は、 [Power BI コミュニティ](https://community.powerbi.com/)を利用してください。

