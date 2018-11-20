---
title: オンプレミスのデータ ソースにシングル サインオン (SSO) を使用する
description: Power BI からオンプレミス データ ソースへのシングル サインオン (SSO) を有効にするようにゲートウェイを構成します。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 10/15/2018
LocalizationGroup: Gateways
ms.openlocfilehash: b728ba6ebaab81ea475f51b9134de34c37d4149b
ms.sourcegitcommit: 3b1a1f55465e5dca88783046c6b4c073e4e22e4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51580496"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Power BI のゲートウェイ用シングル サインオン (SSO) の概要

オンプレミスのデータ ゲートウェイと、Kerberos で制約される委任か Security Assertion Markup Language (SAML) を構成することにより、シームレスなシングル サインオン接続を確立し、Power BI のレポートとダッシュボードをオンプレミスのデータで更新できます。 オンプレミス データ ゲートウェイにより、DirectQuery を使う SSO が容易になります。この場合、オンプレミスのデータ ソースへの接続に使われます。

現在サポートされているデータ ソースは次のとおりです。

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) と [SAML](service-gateway-sso-saml.md))
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md)
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

ユーザーが Power BI サービスで DirectQuery レポートを操作すると、クロスフィルター、スライス、並べ替え、レポート編集の各操作で、基になるオンプレミス データ ソースに対してクエリがライブ実行される場合があります。  データ ソースに SSO が構成されていると、Power BI を操作しているユーザーの ID でクエリが実行されます (つまり、Web エクスペリエンスまたは Power BI モバイル アプリで)。 これにより、各ユーザーには、そのユーザーが基になるデータ ソースでアクセス許可を持っているデータだけが表示されます。シングル サインオンを構成すると、異なるユーザー間で共有されるデータ キャッシュはありません。

## <a name="query-steps-when-running-sso"></a>SSO を実行するときのクエリ ステップ

SSO を使ったクエリ実行は、次の図に示す 3 つのステップで構成されます。

![SSO クエリ ステップ](media/service-gateway-sso-overview/sso-query-steps.png)

> [!NOTE]
> Oracle 用の SSO は、まだ有効になっていませんが、開発中であり近日公開予定です。

これらの手順の詳細を次に示します。

1. 各クエリに対し、**Power BI サービス**は構成されたゲートウェイに送信するクエリ要求に*ユーザー プリンシパル名* (UPN) を組み込みます。

2. ゲートウェイは、Azure Active Directory の UPN を Active Directory のローカル ID にマップする必要があります。

   a.  Azure AD DirSync (*Azure AD Connect* とも呼ばれる) が構成されている場合は、マッピングがゲートウェイで自動的に動作します。

   b.  それ以外の場合、ゲートウェイは、ローカルの Active Directory ドメインに対して検索を実行することにより、Azure AD UPN を参照し、これをローカル ユーザーにマップします。

3. ゲートウェイ サービスのプロセスは、マップされたローカル ユーザーを偽装して、基になるデータベースへの接続を開き、クエリを送信します。 ゲートウェイはデータベースと同じコンピューターにインストールされている必要はありません。

## <a name="next-steps"></a>次の手順

SSO の基本を理解したところで、Kerberos と SAML に関する詳細をお読みください。

* [シングル サインオン (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [シングル サインオン (SSO) - SAML](service-gateway-sso-saml.md)
