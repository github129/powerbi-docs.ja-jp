---
title: エラー:Excel ブックにデータが見つかりませんでした。
description: エラー:Excel ブックにデータが見つかりませんでした。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 849c377a140cd0dd31f55760987336fc3711bc79
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285862"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>エラー:Excel ブックにデータが見つかりませんでした。

>[!NOTE]
>この記事は、Excel 2007 以降に適用されます。

Power BI に Excel ブックをインポートするとき、次のエラーが生じることがあります。

*エラー:Excel ブックにデータが見つかりませんでした。データが適切にフォーマットされていない可能性があります。Excel でブックを編集し、再度インポートする必要があります。*

![ブックにデータが見つからない](media/service-admin-troubleshoot-excel-workbook-data/pbi_wecouldntfindanydata.png)

## <a name="quick-solution"></a>クイック ソリューション
1. Excel でブックを編集します。
2. データを含むセルの範囲を選択します。 最初の行には、列のヘッダー (列名) が含まれている必要があります。
3. **Ctrl + T** キーを押して、テーブルを作成します。
4. ブックを保存します。
5. Power BI に戻り、ブックを再びインポートします。または、Excel 2016 を使用していて、ブックを OneDrive for Business に保存した場合は、Excel で [ファイル]、[発行] の順にクリックします。

## <a name="details"></a>詳細
### <a name="cause"></a>原因
Excel では、特定のセルの範囲から**テーブル**を作成できます。これにより、並べ替え、フィルター処理、およびデータの書式設定が簡単になります。

Excel ブックをインポートするとき、Power BI はそれらのテーブルを検索してデータセットにインポートします。テーブルが見つからない場合は、このエラー メッセージが表示されます。

### <a name="solution"></a>解決方法
1. Excel でブックを開きます。 
    >[!NOTE]
    >この図は Excel 2013 のものです。 他のバージョンを使用している場合、表示は少し異なりますが、手順は同じです。
    
    ![ブックを開く](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht1.png)
2. データを含むセルの範囲を選択します。 最初の行には、列のヘッダー (列名) が含まれている必要があります。
   
    ![セルの範囲の選択](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht2.png)
3. **[挿入]** タブのリボンで、**[テーブル]** をクリックします  (または、ショートカットの **Ctrl + T** キーを押します)。
   
    ![テーブルの挿入](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht3.png)
4. 次のダイアログ ボックスが表示されます。 **[先頭行をテーブルの見出しとして使用する]** にチェックマークが付いていることを確認して、**[OK]** を選択します。
   
    ![テーブルの作成](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlcreatetbl.png)
5. これで、データはテーブルとして書式設定されました。
   
    ![テーブルとして書式設定されたデータ](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xltbl.png)
6. ブックを保存します。
7. Power BI に戻ります。 左側のナビゲーション ウィンドウの下部にある [データの取得] を選択します。
   
    ![データの取得](media/service-admin-troubleshoot-excel-workbook-data/pbi_getdata.png)
8. **[ファイル]** ボックスで、 **[取得]** を選択します。
   
    ![ファイルの取得](media/service-admin-troubleshoot-excel-workbook-data/pbi_getfiles.png)
9. Excel ブックを再度インポートします。 今回は、インポートでテーブルが見つかり、成功するはずです。
   
    インポートがまだ失敗する場合は、ヘルプ メニューの **[コミュニティ]** をクリックして通知してください。
   
    ![[コミュニティ] リンク](media/service-admin-troubleshoot-excel-workbook-data/pbi_questionmenucommunity.png)
