---
title: Power BI Premium の大規模なモデル (プレビュー)
description: 大規模なモデルの機能を使用すると、Power BI Premium のデータセットのサイズを 10 GB 以上に拡張することができます。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/29/2019
LocalizationGroup: Premium
ms.openlocfilehash: a561976a968284197f759f60c621a757f2995f4f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881164"
---
# <a name="large-models-in-power-bi-premium-preview"></a>Power BI Premium の大規模なモデル (プレビュー)

Power BI データセットでは、クエリ パフォーマンスが最適化されるように、データを圧縮率の高い、メモリ内キャッシュに格納できます。 これにより、大規模なデータセットに対するユーザーの操作が高速化されます。 大規模なモデルの機能を使用すると、Power BI Premium のデータセットのサイズを 10 GB 以上に拡張することができます。 その代わり、データセットのサイズは Power BI Premium の容量サイズによって制限されます。 これは、Azure Analysis Services がモデル サイズの制限において機能するしくみと似ています。 Power BI Premium における容量サイズの詳細については、容量ノードに関するページを参照してください。 すべての Premium P SKU と Embedded A SKU で大規模なモデルを設定できますが、これは[新しいワークスペース](service-create-the-new-workspaces.md)でのみ機能します。

大規模なモデルは PBIX のアップロード サイズには影響しません。これは現在も 10 GB に制限されています。 その代わり、データセットは更新時にサービス内で 10 GB を超えてもかまいません。 増分更新を使用して、10 GB を超えるサイズのデータセットを構成できます。

## <a name="enable-large-models"></a>大規模なモデルを有効にする

10 GB を超えるデータセットを作成するには、次の手順を実行します。

1. Power BI Desktop でデータセットを作成し、[増分更新](service-premium-incremental-refresh.md)を構成します。

1. データセットを Power BI Premium サービスに発行します。

1. 下の PowerShell コマンドレットを実行して、大規模なモデルのデータセットを有効にします。 これらのコマンドレットを実行すると、Power BI ではそのデータセットが Azure Premium ファイルに格納され、10 GB の制限が適用されなくなります。

1. 更新を呼び出し、増分更新ポリシーに基づいて履歴データを読み込みます。 最初の更新では、履歴の読み込みに時間がかかる場合があります。 その後の更新は増分であるため、時間は短縮されます。

### <a name="powershell-cmdlets"></a>PowerShell コマンドレット

現在のバージョンの大規模なモデルで、PowerShell コマンドレットを使用して、Premium ファイル ストレージのデータセットを有効にします。 PowerShell コマンドレットを実行するには、容量管理者とワークスペース管理者の特権が必要です。

1. データセット ID (GUID) を確認します。 ワークスペースの **[データセット]** タブで、データセットの設定の下にある URL に ID が表示されます。

    ![データセット GUID](media/service-premium-large-models/dataset-guid.png)

1. PowerShell 管理者プロンプトで、[MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/) モジュールをインストールします。

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. 次のコマンドレットを実行してサインインし、データセットのストレージ モードを確認します。

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    応答は次のようになります。 このストレージ モードは ABF (Analysis Services のバックアップ ファイル) です。これは既定値です。

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. 次のコマンドレットを実行して、ストレージ モードを Premium ファイルに設定し、これを確認します。 Premium ファイルへの変換には、数秒かかることがあります。

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    応答は次のようになります。 ストレージ モードが Premium ファイルに設定されました。

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

[Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus) コマンドレットを使用すると、Premium ファイルとの間のデータセットの変換状態を確認できます。

## <a name="dataset-eviction"></a>データセットの削除

Power BI では、動的メモリ管理を使用して、非アクティブなデータセットをメモリから削除します。 Power BI はデータセットを削除することで、ユーザー クエリに対処するために他のデータセットを読み込むことができます。 動的メモリ管理を使用すると、データセットのサイズの合計をその容量で使用可能なメモリよりも大幅に大きくすることができますが、1 つのデータセットはメモリに収める必要があります。 動的メモリ管理の詳細については、「[容量はどのように機能するのか](service-premium-what-is.md#how-capacities-function)」を参照してください。

削除による大規模なモデルへの影響を考慮する必要があります。 データセットの読み込み時間は比較的短いにもかかわらず、ユーザーは削除された大規模なデータセットの再読み込みを待つ必要がある場合に顕著な遅延が発生する可能性があります。 このため、現在の形では、大規模なモデルの機能は、セルフサービス BI 要件と混在したものではなく、主にエンタープライズ BI 要件専用の容量に対して使用することが推奨されます。 エンタープライズ BI 要件専用の容量では、削除が頻繁にトリガーされる可能性や、データセットの再読み込みが必要になる可能性は低くなります。 その一方、セルフサービス BI 用の容量には、メモリへの読み込みやメモリからの読み込みの頻度が高い小さなデータセットが数多く格納されています。

## <a name="checking-dataset-size"></a>データセット サイズの確認

履歴データを読み込んだ後、[XMLA エンドポイント](service-premium-connect-tools.md)を介して [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) を使用して、モデルのプロパティ ウィンドウでデータセットの推定サイズを確認できます。

![データセットの推定サイズ](media/service-premium-large-models/estimated-dataset-size.png)

また、SSMS から次の DMV クエリを実行することによってデータセットのサイズを確認できます。 出力の DICTIONARY\_SIZE 列と USED\_SIZE 列を合計し、データセットのサイズ (バイト単位) を確認します。

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="current-feature-restrictions"></a>現在の機能の制限事項

大規模なモデルを使用する場合は、次の制限事項に留意してください。

- **Bring Your Own Key (BYOK) 暗号化**: Premium ファイルに対して有効化したデータセットは、[BYOK](service-encryption-byok.md) では暗号化されません。
- **Multi-geo のサポート**: Premium ファイルに対して有効になっているデータセットは、[Multi-geo](service-admin-premium-multi-geo.md) も有効になっている容量で失敗します。

- **Power BI Desktop へのダウンロード**: データセットが Premium ファイルに格納されている場合、[.pbix ファイルとしてのダウンロード](service-export-to-pbix.md)は失敗します。
- **サポートされているリージョン**: 大規模なモデルは、次のリージョンでサポートされています。
  - オーストラリア東部
  - オーストラリア南東部
  - 米国中部
  - 東アジア
  - 米国東部
  - 米国東部 2
  - 東日本
  - 西日本
  - 韓国中部
  - 韓国南部
  - 米国中北部
  - 北ヨーロッパ
  - 米国中南部
  - 東南アジア
  - 英国南部
  - 英国西部
  - 西ヨーロッパ
  - 米国西部
  - 米国西部 2