---
title: 動的バインドを使用してレポートをデータセットに接続する
description: 動的バインドを使用してレポートを埋め込む方法について学習します。
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: ecc7ec21117c9e2cd974058c63bcf02d72d1f4b1
ms.sourcegitcommit: 50c4bebd3432ef9c09eacb1ac30f028ee4e66d61
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925755"
---
# <a name="connecting-a-report-to-a-dataset-using-dynamic-binding"></a>動的バインドを使用してレポートをデータセットに接続する 

動的バインドの使用は、レポートがデータセットに接続されている場合にのみ関係します。 レポートとデータセット間の接続は、*バインド*と呼ばれます。 事前に定義されたものではなく、埋め込みの時点でバインドが決定されると、そのバインドは[動的バインド](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FLate_binding&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C5d5b0d2d62cf4818f0c108d7635b151e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637087115150775585&sdata=AbEtdJvgy4ivi4v4ziuui%2Bw2ibTQQXBQNYRKbXn5scA%3D&reserved=0)と呼ばれます。
 
*動的バインド*を使用して Power BI レポートを埋め込む場合は、同じレポートをユーザーの資格情報に応じて異なるデータセットに接続することができます。
 
これは、1 つのレポートを使用し、接続されているデータセットに応じて、異なる情報を表示できることを意味します。 たとえば、小売店の売上の値を示すレポートを別の小売業者のデータセットに接続し、接続されている小売業者のデータセットに応じて、異なる結果を生成することができます。
 
レポートとデータセットは、必ずしも同じワークスペースに存在している必要はありません。 両方のワークスペース (レポートが含まれるものとデータセットが含まれるもの) が、[容量](azure-pbie-create-capacity.md)に割り当てられている必要があります。

埋め込みプロセスの一環として、*十分なアクセス許可を持つトークンを確実に生成し*、*構成オブジェクトを調整します*。


## <a name="generating-a-token-with-sufficient-permissions"></a>十分なアクセス許可を持つトークンを生成する

動的バインドは、*組織向けの埋め込み*と*顧客向けの埋め込み*の両方のシナリオでサポートされます。 次の表では、各シナリオの考慮事項について説明します。


|シナリオ  |データ所有権  |トークン  |要件  |
|---------|---------|---------|---------|
|*組織向けの埋め込み*    |ユーザー所有データ         |Power BI ユーザーのアクセス トークン         |使用する Azure AD トークンを所有するユーザーには、すべての成果物に対する適切なアクセス許可があることが必要です。         |
|*顧客向けの埋め込み*     |アプリ所有データ         |Power BI ユーザーではないユーザーのアクセス トークン         |レポートと動的にバインドされたデータセットの両方に対するアクセス許可を含んでいることが必要です。 複数の成果物をサポートする埋め込みトークンを生成するには、[複数の項目の埋め込みトークンを生成するための API](embed-sample-for-customers.md#multiEmbedToken) を使用します。         |

## <a name="adjusting-the-config-object"></a>構成オブジェクトを調整する
構成オブジェクトに `datasetBinding` を追加します。 次の例を参照として使用します。

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>次の手順

Power BI での埋め込みに馴染みのない方は、Power BI のコンテンツを埋め込む方法を次のチュートリアルでご覧いただけます。
* [チュートリアル:顧客向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-customers.md)
* [チュートリアル:組織向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-your-organization.md)