---
title: Power BI モバイル アプリでバーコードをスキャンする
description: 現実世界でバーコードをスキャンし、Power BI モバイル アプリでフィルターされた BI 情報に直接アクセスできます。
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: mshenhav
ms.openlocfilehash: bbc787203293fc6c9075400abf674345710faaed
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879175"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>デバイスで Power BI モバイル アプリからバーコードをスキャンする
現実世界でバーコードをスキャンし、Power BI モバイル アプリでフィルターされた BI 情報に直接アクセスできます。


適用対象:

| ![iPhone](./media/mobile-apps-quickstart-view-dashboard-report/iphone-logo-30-px.png) | ![Android](./media/mobile-apps-quickstart-view-dashboard-report/android-logo-30-px.png) | 
|:--- |:--- |
| iPhone | Android (スマートフォン、タブレット) | 

たとえば、同僚が [Power BI Desktop のレポートのバーコード フィールドにタグを付け](../../desktop-mobile-barcodes.md)、そのレポートを自分と共有したとします。 

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

デバイスの Power BI アプリのスキャナーで製品バーコードをスキャンすると、そのバーコードのレポート (またはレポートの一覧) が表示されます。 そのバーコードにフィルター処理されたレポートを開くことができます。

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Power BI スキャナーでバーコードをスキャンする
1. Power BI モバイル アプリで、左上のメイン ナビゲーション メニュー ![](media/mobile-apps-scan-barcode-iphone/pbi_iph_navmenu.png) を開きます。 
2. **スキャナー** まで下にスクロールし、それを選択します。 
   
    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)
3. カメラが有効になっていない場合は、Power BI アプリでカメラを使用することを承認する必要があります。 これは、1 回限りの承認です。 
4. 製品のバーコードをスキャナーでポイントします。 
   
    そのバーコードに関連付けられたレポートの一覧が表示されます。
5. そのバーコードに自動的にフィルター処理されたレポート名をタップして、デバイスで開きます。

## <a name="filter-by-other-barcodes-while-in-a-report"></a>レポートを開いているときに他のバーコードでフィルターする
あるバーコードでフィルター処理されたレポートをデバイスで表示しているときに、そのレポートを別のバーコードでフィルター処理したい場合があります。

* バーコード アイコンにフィルター ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) がある場合、フィルターがアクティブになり、レポートをバーコードでフィルターすることができます。 
* アイコンにフィルター ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png) が含まれていない場合、フィルターはアクティブにならず、レポートはバーコードでフィルターされません。 

いずれの方法でも、アイコンをタップすると浮動スキャナーがある小さなメニューが開きます。

* スキャナーを新しい項目に移動すると、レポートのフィルターは別のバーコード値に変わります。 
* フィルターされていないレポートに戻るには、 **[Clear barcode filter]** (バーコード フィルターのクリア) を選択します。
* レポート フィルターを、現在のセッション内でスキャンしたバーコードのいずれかに変更するには、 **[Filter by recent barcodes]** (最近のバーコードでフィルター) を選択します。

## <a name="issues-with-scanning-a-barcode"></a>バーコードのスキャンに関する問題
ここでは、製品でバーコードをスキャンするときに表示される可能性があるメッセージについて説明します。

### <a name="couldnt-filter-report"></a>"レポートをフィルター処理できませんでした..."
フィルター対象に選択したレポートは、このバーコード値を含まないデータ モデルに基づいています。 たとえば、レポートに "mineral water" という製品が含まれていません。  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>レポートのすべてまたは一部のビジュアルに値が含まれていない
スキャンしたバーコード値はモデル内に存在しますが、レポートのすべてまたは一部のビジュアルに、この値が含まれていないため、フィルターから空の状態が返されます。 他のレポート ページを見るか、Power BI デスクトップでレポートを編集してこの値を含めます。 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>"バーコードでフィルターをかけられるレポートはお持ちでないようです。"
これは、バーコード対応のレポートがないことを示します。 バーコード スキャナーは、 **[バーコード]** とマークされた列があるレポートのみをフィルターできます。  

自分またはレポート所有者が Power BI Desktop で列に **[バーコード]** とタグを付けていることを確認します。 詳細については、[Power BI Desktop でバーコード フィールドにタグを付ける方法](../../desktop-mobile-barcodes.md)に関するページを参照してください。

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>"レポートをフィルター処理できませんでした - このバーコードはレポート データに存在しないようです。"
フィルター対象に選択したレポートは、このバーコード値を含まないデータ モデルに基づいています。 たとえば、レポートに "mineral water" という製品が含まれていません。 別の製品をスキャンする、別のレポートを選択する (複数のレポートを使用できる場合)、またはフィルターされていないレポートを表示することができます。 

## <a name="next-steps"></a>次の手順
* [Power BI Desktop のバーコード フィールドにタグを付ける](../../desktop-mobile-barcodes.md)
* [Power BI のダッシュボードのタイル](../end-user-tiles.md)
* [Power BI のダッシュボード](../end-user-dashboards.md)

