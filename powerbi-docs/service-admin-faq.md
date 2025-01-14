---
title: Power BI の管理 - よく寄せられる質問 (FAQ)
description: Power BI のサインアップ、テナント管理、その他の管理タスクに関するよく寄せられる質問 (FAQ) とその回答について説明します。
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 711646009fe79e145a3ab756266a442243c1116e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73857824"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Power BI の管理 - よく寄せられる質問 (FAQ)

この記事では、Power BI の管理に関するよく寄せられる質問 (FAQ) を取り上げます。 Power BI の管理の概要については、[Power BI の管理](service-admin-administering-power-bi-in-your-organization.md)に関するページを参照してください。

## <a name="whats-in-this-article"></a>この記事の内容

### <a name="sign-up-for-power-bi-section"></a>Power BI のサインアップ セクション

* [PowerShell の使用](#using-powershell)
* [ユーザーは Power BI にどのような方法でサインアップできますか。](#how-do-users-sign-up-for-power-bi)
* [組織内の個々のユーザーは、どのような方法でサインアップできますか。](#how-do-individual-users-in-my-organization-sign-up)
* [既存の Office 365 テナントにユーザーが参加できないようにするにはどうすればよいですか。](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [既存の Office 365 テナントへの参加をユーザーに許可するにはどうすればよいですか。](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [テナントをブロックしたかどうかを確認するにはどうすればよいですか。](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [既存のユーザーが Power BI の使用を開始できないようにするにはどうすればよいですか。](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [既存のユーザーに Power BI へのサインアップを許可するにはどうすればよいですか。](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Power BI の管理セクション

* [組織内のユーザーの ID を管理する方法はどのように変わりますか。](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Power BI を管理するにはどうすればよいですか。](#how-do-we-manage-power-bi)
* [Microsoft によってユーザーに対して作成されたテナントを管理するにはどうすればよいですか。](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [複数のドメインがある場合、ユーザーが追加される Microsoft 365 テナントを制御できますか。](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Power BI に既にサインアップしているユーザーを削除するにはどうすればよいですか。](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [新しいユーザーがいつテナントに参加したかを確認するにはどうすればよいですか。](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [他に何か準備する必要があることはありますか。](#are-there-any-additional-things-i-should-prepare-for)
* [Power BI テナントの場所](#where-is-my-power-bi-tenant-located)
* [Power BI SLA (サービス レベル アグリーメント) とは何ですか。](#what-is-the-power-bi-sla)
* [Power BI では高可用性とフェールオーバーはどのように処理されますか。](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Power BI のセキュリティ セクション

* [Power BI は、国、地域、および業界固有のコンプライアンス要件を満たしていますか。](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Power BI のセキュリティはどのように機能していますか。](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Power BI にサインアップする

### <a name="using-powershell"></a>PowerShell の使用

このセクションの一部の手順では、Windows PowerShell スクリプトが必要です。 PowerShell に慣れていない場合は、「[Windows PowerShell ファースト ステップ ガイド](https://go.microsoft.com/fwlink/p/?LinkID=286814)」を読むことをお勧めします。 スクリプトを実行するには、最初に [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/) の最新の 64 ビット バージョンをインストールします。

### <a name="how-do-users-sign-up-for-power-bi"></a>ユーザーは Power BI にどのような方法でサインアップできますか。

Microsoft 365 管理者は、[Power BI Web サイト](https://powerbi.microsoft.com)または Microsoft 365 管理センターの[サービス購入](https://admin.microsoft.com/AdminPortal/Home#/catalog)ページから、Power BI にサインアップすることができます。 Microsoft 365 管理者が Power BI にサインアップした場合は、アクセスする必要があるユーザーにユーザー ライセンスを割り当てることができます。

さらに、組織内の個々のユーザーは、[Power BI Web サイト](https://powerbi.microsoft.com)から Power BI にサインアップすることができます。 組織内のユーザーが Power BI にサインアップすると、そのユーザーに Power BI ライセンスがサービスによって自動的に割り当てられます。 詳しくは、「[個人として Power BI にサインアップする](service-self-service-signup-for-power-bi.md)」および「[組織での Power BI のライセンス](service-admin-licensing-organization.md)」をご覧ください。

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>組織内の個々のユーザーは、どのような方法でサインアップできますか。

組織内のユーザーに適用される可能性がある 3 つのシナリオがあります。

* **シナリオ 1**:組織に既存の Microsoft 365 環境が既に存在し、Power BI にサインアップするユーザーが Microsoft 365 アカウントを既に持っている。
    このシナリオでは、ユーザーがテナント (contoso.com など) に既に職場または学校のアカウントを持っているが、まだ Power BI にサインアップしていない場合は、Microsoft がそのアカウントに対して Power BI Free プランをアクティブ化します。 Power BI サービスの使用方法に関する通知が自動的にユーザーに送信されます。

* **シナリオ 2**:組織に既存の Microsoft 365 環境が既に存在するが、Power BI にサインアップするユーザーがまだ Microsoft 365 アカウントを持っていない場合。
    このシナリオでは、ユーザーは、組織のドメイン (contoso.com など) のメール アドレスを持っていますが、まだ Microsoft 365 アカウントを持っていません。 この場合、ユーザーは Power BI にサインアップすることができ、アカウントが自動的に与えられます。 このアクションにより、ユーザーは、Power BI サービスにアクセスすることができます。 たとえば、Nancy という名前の従業員が職場のメール アドレス (nancy@contoso.com など) を使用してサインアップした場合、Contoso の Microsoft 365 環境に Nancy がユーザーとして自動的に追加され、そのアカウントに対して Power BI が有効になります。

* **シナリオ 3**:メール ドメインに接続されている Microsoft 365 環境が組織にない。
    Power BI を利用するために組織が行う必要がある管理操作はありません。 ユーザーは、そのサービスによって新しいクラウド専用のユーザー ディレクトリに追加されます。 テナントの Microsoft 365 全体管理者として引き継いで、それらを管理することもできます。

> [!IMPORTANT]
> 組織に複数の電子メール ドメインがあり、すべての電子メール アドレスの拡張を同じテナントにまとめる場合は、ユーザーがサインアップする前に、すべての電子メール アドレス ドメインを Azure Active Directory テナントに追加する必要があります。 ユーザーを作成した後、テナント間でユーザーを自動的に移動するメカニズムはありません。 このプロセスについて詳しくは、この記事で後述する「[複数のドメインがある場合、ユーザーが追加される Microsoft 365 テナントを制御できますか](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)」と、[Microsoft 365 にドメインを追加する方法](/office365/admin/setup/add-domain/)に関するページを参照してください。

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>既存の Microsoft 365 テナントにユーザーが参加できないようにするにはどうすればよいですか。

既存の Microsoft 365 テナントにユーザーが参加できないようにするために、Microsoft 365 全体管理者として実行できる手順があります。 アクセスをブロックした場合、ユーザーのサインアップ試行は失敗し、ユーザーに組織の管理者に連絡するように指示するメッセージが表示されます。ライセンスの自動配布 (学生、教職員、およびスタッフ向けの Office 365 for Education など) を既に無効にしている場合は、このプロセスを繰り返す必要はありません。

新しいユーザーがマネージド テナントに参加できないようにするには、次の PowerShell スクリプトを使用します。 ([PowerShell の詳細を確認する][1]。)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> アクセスをブロックすると、組織内の新しいユーザーは Power BI にサインアップできなくなります。 組織の新しいサインアップを無効にする前に Power BI にサインアップしているユーザーは、引き続きライセンスを保持します。 ユーザーを削除する方法については、後の「[Power BI に既にサインアップしているユーザーを削除するにはどうすればよいですか](#how-do-i-remove-power-bi-for-users-that-already-signed-up)」をご覧ください。

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>既存の Microsoft 365 テナントへの参加をユーザーに許可するにはどうすればよいですか。

新しいユーザーがマネージド テナントに参加できるようにするには、次の PowerShell スクリプトを使用します。 ([PowerShell の詳細を確認する][1]。)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>テナントをブロックしたかどうかを確認するにはどうすればよいですか。

設定を確認するには、次の PowerShell スクリプトを使用します。 *AllowEmailVerifiedUsers* が false になっている必要があります。 ([PowerShell の詳細を確認する][1]。)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>既存のユーザーが Power BI の使用を開始できないようにするにはどうすればよいですか。

これを制御する Azure AD の設定は、**AllowAdHocSubscriptions** です。 ほとんどのテナントでは、これは、有効を意味する *true* に設定されます。 パートナーを通じて Power BI を入手した場合、これは、無効を意味する *false* に設定されている可能性があります。

アドホック サブスクリプションを無効にするには、次の PowerShell スクリプトを使用します ([PowerShell の詳細を確認する][1])。

1. Microsoft 365 の資格情報を使用して Azure Active Directory にサインインします。 次の PowerShell のスクリプトの 1 行目では、ユーザーに資格証明が要求されます。 2 行目で、Azure Active Directory に接続します。

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![PowerShell を使用した Azure Active Directory サインインのスクリーンショット](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. サインインの後、次のコマンドを実行してテナントの現在のセットアップ内容を確認することができます。

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. 次のコマンドを使用して、**AllowAdHocSubscriptions** を有効 (`$true`) または無効 (`$false`) にします。

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> **AllowAdHocSubscriptions** フラグは、組織内のさまざまなユーザーの能力を制御するために使用されます。この中には、ユーザーが Azure Rights Management サービスにサインアップする能力も含まれます。 このフラグの変更は、これらすべての能力に影響します。 設定が *false* の場合でも、ユーザーは個人用 Power BI Pro 試用版にサインアップすることができます。

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>既存のユーザーに Power BI へのサインアップを許可するにはどうすればよいですか。

既存のユーザーに Power BI へのサインアップを許可するには、前の質問で説明されているコマンドを実行しますが、最後のステップで `$false` の代わりに `$true` を渡します。

## <a name="administration-of-power-bi"></a>Power BI の管理

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>組織内のユーザーの ID を管理する方法はどのように変わりますか。

組織内のユーザーに適用される可能性がある 3 つのシナリオがあります。

* **シナリオ 1**:組織に既存の Microsoft 365 環境があり、組織内のすべてのユーザーが Microsoft 365 アカウントを持っている場合、ID の管理方法に変更はありません。

* **シナリオ 2**:組織に既存の Microsoft 365 環境は既に存在するが、組織内の一部のユーザーのみが Microsoft 365 アカウントを持っている場合は、テナント内にユーザーが作成され、ユーザーの職場または学校のメール アドレスに基づいてライセンスが割り当てられます。

    その結果、組織内のユーザーがサービスにサインアップすると、その時点で管理しているユーザーの数が増加します。

* **シナリオ 3**:メール ドメインに接続された Microsoft 365 環境が組織にない場合は、ID の管理方法に変更はありません。

    ユーザーは、新しいクラウド専用ユーザー ディレクトリに追加されます。そのディレクトリを Microsoft 365 全体管理者が引き継いでユーザーを管理するよう選択できます。

### <a name="how-do-we-manage-power-bi"></a>Power BI を管理するにはどうすればよいですか。

Power BI には、Microsoft 365 全体管理者ロールのユーザーと Power BI サービス管理者ロールのユーザーとを対象とした Power BI 管理ポータルが用意されています。 Power BI 管理ポータルを使用するには、自分のアカウントを Microsoft 365 または Azure Active Directory 内で**全体管理者**としてマークしておくか、自分のユーザー アカウントに別のユーザーが Power BI サービス管理者ロールを割り当てている必要があります。 詳しくは、[Power BI 管理者ロールについて](service-admin-role.md)および [Power BI 管理ポータル](service-admin-portal.md)についての記事をご覧ください。 ポータルには、テナント全体の設定を制御する機能や、Power BI の使用状況の統計を表示する機能、ユーザーとグループを管理するための Microsoft 365 管理センターへのリンクが用意されています。

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Microsoft によってユーザーに対して作成されたテナントを管理するにはどうすればよいですか。

セルフサービスのユーザーは、Azure AD を使用しているクラウド サービスにサインアップするとき、サービスによってユーザーは、各自の電子メール ドメインに基づいて Azure AD のアンマネージド ディレクトリに追加されます。 "*管理者引き継ぎ*" と呼ばれるプロセスを使って別のユーザーが作成したテナントを要求し、管理することができます。 詳細については、「[Azure Active Directory の非管理対象ディレクトリを管理者として引き継ぐ](/azure/active-directory/users-groups-roles/domains-admin-takeover)」をご覧ください。 実行する引き継ぎの種類は、ご自身のドメインに関連付けられている既存のマネージド テナントが存在するかどうかによって異なります。

* Power BI では、内部管理者の引き継ぎがサポートされています。 アンマネージド Azure ディレクトリの "_内部_" 管理者の引き継ぎを実行すると、アンマネージド ディレクトリのグローバル管理者として追加されます。 ユーザー、ドメイン、またはサービス プランは、管理対象の他のディレクトリには移行されません。

* Power BI では、外部管理者の引き継ぎはサポートされなくなりました。 アンマネージド Azure ディレクトリの "_外部_" 管理者の引き継ぎを実行すると、アンマネージド ディレクトリの DNS ドメイン名が、マネージド Azure ディレクトリに追加されます。 外部の引き継ぎが行われると、元のアンマネージド テナント上の Power BI コンテンツには一切アクセスできなくなります。 Power BI レポートは、新しいテナントに再発行する必要があります。また、Power BI ダッシュボードとアプリは、新しいテナントに作成し直す必要があります。

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>複数のドメインがある場合、ユーザーが追加される Microsoft 365 テナントを制御できますか。

何もしなければ、各ユーザーの電子メール ドメインとサブドメイン用のテナントがサービスによって作成されます。 電子メール アドレスの拡張に関係なく、すべてのユーザーを同じテナントにまとめる場合:事前に対象テナントを作成するか、既存のテナントを使用します。 次に、そのテナントに含める既存のドメインとサブドメインをすべて追加します。 電子メール アドレスの末尾がこれらのドメインとサブドメインに該当するすべてのユーザーは、サインアップ時に自動的に対象テナントに追加されます。

> [!IMPORTANT]
> ユーザーを作成した後、テナント間でユーザーを自動的に移動するメカニズムはサポートされていません。 1 つの Microsoft 365 テナントにドメインを追加する方法については、[Office 365 へのユーザーとドメインの追加](/office365/admin/setup/add-domain/)に関するページを参照してください。

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Power BI に既にサインアップしているユーザーを削除するにはどうすればよいですか。

Power BI にサインアップする必要がなくなったユーザーが Power BI にアクセスできないようにする場合は、そのユーザーの Power BI ライセンスを削除できます。

1. [Microsoft 365 管理センター](https://admin.microsoft.com/AdminPortal/Home#/homepage)に移動します。

1. ナビ ペインで、 **[ユーザー]**  >  **[アクティブ ユーザー]** の順に選択します。

1. ライセンスを削除するユーザーを見つけ、その名前を選択します。

    ユーザーのライセンスは、一括管理することもできます。 これを実行するには、複数のユーザーを選択し、 **[製品ライセンスを編集]** を選択します。

1. ユーザーの詳細ウィンドウで、 **[製品ライセンス]** の隣にある **[編集]** を選択します。

1. アカウントに適用されているライセンスに応じて、 **[Power BI (無料)]** または **[Power BI Pro]** を **[オフ]** に設定します。

1. **[保存]** を選択します。

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>新しいユーザーがいつテナントに参加したかを確認するにはどうすればよいですか。

セルフ サービス サインアップでテナントに参加したユーザーには、管理ダッシュボードの [アクティブ ユーザー] ペインでフィルター処理することができる一意のライセンスが割り当てられます。 この新しいビューを作成するには、次の手順のようにします。

1. [Microsoft 365 管理センター](https://admin.microsoft.com/AdminPortal/Home#/homepage)に移動します。

1. ナビ ペインで、 **[ユーザー]**  >  **[アクティブ ユーザー]** の順に選択します。

1. **[ビュー]** メニューの **[カスタム ビューの追加]** を選択します。

1. 新しいビューに名前を付け、 **[割り当て済みの製品ライセンス]** で、 **[Power BI (無料)]** または **[Power BI Pro]** を選択します。

    ビューごとにライセンスを 1 つだけ選択できます。 組織内に **Power BI (無料)** のライセンスと **Power BI Pro** のライセンスがある場合は、2 つのビューを作成できます。

1. 他の必要な条件を入力した後、 **[追加]** を選択します。

1. 新しく作成したビューは、 **[ビュー]** メニューから使用できます。

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>他に何か準備する必要があることはありますか。

パスワードのリセット要求が増える可能性があります。 このプロセスの詳細については、[ユーザーのパスワードを再設定する](/office365/admin/add-users/reset-passwords)ことに関する記事を参照してください。

テナントからのユーザーの削除は、Microsoft 365 管理センターの標準的なプロセスを使用して実行できます。 ただし、ユーザーが組織のアクティブなメール アドレスを引き続き使用する場合、すべてのユーザーがブロックされない限り、そのユーザーはテナントに再び参加できます。

### <a name="where-is-my-power-bi-tenant-located"></a>Power BI テナントの場所

Power BI テナントが存在するデータ リージョンについて詳しくは、「[Power BI テナントの場所](service-admin-where-is-my-tenant-located.md)」をご覧ください。

### <a name="what-is-the-power-bi-sla"></a>Power BI SLA とは何ですか。

Power BI SLA (サービス レベル アグリーメント) については、Microsoft ライセンス Web サイトの「**ライセンス**」セクションにある「[ライセンス条項とドキュメント](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37)」という記事をご覧ください。

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Power BI では高可用性とフェールオーバーはどのように処理されますか。

高可用性とフェールオーバーの詳細については、「[Power BI の高可用性、フェールオーバー、およびディザスター リカバリーに関する FAQ](service-admin-failover.md)」を参照してください。

## <a name="security-in-power-bi"></a>Power BI のセキュリティ

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI は、国、地域、および業界固有のコンプライアンス要件を満たしていますか。

Power BI のコンプライアンスの詳細については、[Microsoft セキュリティ センター](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx)を参照してください。

### <a name="how-does-security-work-in-power-bi"></a>Power BI のセキュリティはどのように機能していますか。

Microsoft は Power BI を Microsoft 365 上に構築しており、Azure Active Directory などの Azure サービス上に構築されます。 Power BI のアーキテクチャの概要については、「[Power BI のセキュリティ](service-admin-power-bi-security.md)」をご覧ください。

## <a name="next-steps"></a>次の手順

[Power BI 管理ポータル](service-admin-portal.md)  
[Power BI 管理者の役割について](service-admin-role.md)  
[Power BI のセルフサービス サインアップ](service-self-service-signup-for-power-bi.md)  
[Power BI Pro を購入する](service-admin-purchasing-power-bi-pro.md)  
[Power BI Premium とは何ですか?](service-premium-what-is.md)  
[Power BI Premium の購入方法](service-admin-premium-purchase.md)  
[Power BI Premium ホワイト ペーパー](https://aka.ms/pbipremiumwhitepaper)  
[Power BI および Office 365 でのグループ管理](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365 のユーザー アカウント管理](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Office 365 グループ管理](/office365/admin/email/create-edit-or-delete-a-security-group/)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

[1]: https://docs.microsoft.com/powershell/scripting/overview
