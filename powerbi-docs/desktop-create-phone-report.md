---
title: モバイル アプリ向けに最適化されたレポートを作成する
description: 縦バージョンのレポートをスマートフォンとタブレット専用に作成して、Power BI モバイル アプリ用にレポート ページを最適化する方法について説明します。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 8808391d0794ec4a487526cc5bbe4216fe0f75a6
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275320"
---
# <a name="create-reports-optimized-for-the-power-bi-mobile-apps"></a>Power BI モバイル アプリ向けに最適化されたレポートを作成する
スマートフォンまたはタブレット上のモバイル アプリでのレポートの表示に関するエクスペリエンスを向上させることができます。 スマートフォンとタブレット専用に、レポートの縦レイアウトを作成します。 Power BI Desktop および Power BI サービスで、縦レイアウトのビジュアルを再配置およびサイズ変更することで、最適なエクスペリエンスにレポートを適応させます。 これらのすべてを含める必要はありません。 さらに、電話上で適切にサイズ変更されて表示される[*レスポンシブ* ビジュアル](#optimize-a-visual-for-any-size)と[レスポンシブ スライサー](#enhance-slicers-to-to-work-well-in-phone-reports)を作成することもできます。 また、レポートにフィルターを追加した場合、これらのフィルターは最適化されたレポートに自動的に表示されます。 レポートの読者は、それを使ってレポートをフィルター処理することができます。

![電話に対して最適化されたレポート](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

## <a name="lay-out-a-portrait-version-of-a-report-page"></a>縦バージョンのレポート ページをレイアウトする

レポートを作成したら、スマートフォンとタブレット用にそれを最適化できます。

1. Power BI Desktop のレポート ビューにある **[表示]** タブで、**[電話レイアウト]** を選択します。  
   
    ![[電話レイアウト] アイコン](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    Power BI サービスで、**[レポートの編集]** > **[モバイル レイアウト]** を選択します。

    スマートフォンのような形の空白のキャンバスが表示されます。 元のレポート ページのすべてのビジュアルが、右側の [視覚化] ウィンドウに表示されます。

3. 電話レイアウトにビジュアルを追加するには、それを [視覚化] ウィンドウから電話キャンバスにドラッグします。
   
    電話レポートは、グリッド レイアウトを使用します。 ビジュアルをモバイル キャンバスにドラッグすると、そのグリッドにスナップされます。
   
    ![ビジュアルのドラッグ アンド ドロップ](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    マスター レポート ページの一部またはすべてのビジュアルを電話レポート ページに追加できます。 各ビジュアルは 1 回だけ追加することができます。

4. ダッシュボードやモバイル ダッシュボード上のタイルの場合と同様に、グリッド上のビジュアルのサイズを変更できます。
   
   電話レポートのグリッドは、さまざまなサイズの電話に向けてスケーリングされます。このため、電話の画面が小さくても大きくても、レポートの見栄えがよくなります。
   
   ![ビジュアル サイズの変更](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>ビジュアルのサイズを最適化する
ダッシュボードまたはレポート内のビジュアルを "*レスポンシブ*" に設定できます。 それらは、画面のサイズに関係なく、最大量のデータと分析情報を表示するために動的に変化できるようになります。 

ビジュアルのサイズが変更されると、Power BI はデータ ビューを優先します。 たとえば、自動的に余白を削除し、凡例をビジュアルの上部に移動する場合があります。このため、ビジュアルは小さくなっても引き続き有益な情報を提供できます。

![レスポンシブ ビジュアルのサイズ変更](media/desktop-create-phone-report/desktop-create-phone-report-6.gif)

ビジュアルごとに応答性を有効にするかどうかを選択します。 詳細については、[ビジュアルの最適化](visuals/desktop-create-responsive-visuals.md)に関するページをご覧ください。

## <a name="considerations-when-creating-phone-report-layouts"></a>電話レイアウトまたはレポート レイアウトを作成する場合の注意事項
* 複数ページのレポートの場合、すべてのページまたは数ページだけを最適化できます。 
* レポート ページの背景色を定義した場合、電話レポートに同じ背景色が設定されます。
* 電話用だけの書式設定を変更することはできません。 書式設定は、マスターとモバイルのレイアウトで一貫しています。 たとえば、フォント サイズは同じになります。
* 書式設定、データセット、フィルター、またはその他の属性の変更など、ビジュアルを変更するには、通常のレポート作成モードに戻ります。
* Power BI は、モバイル アプリの電話レポートに対して既定のタイトルとページ名を指定します。 レポートでタイトルとページ名のテキスト ビジュアルを作成していた場合は、それらを電話レポートに追加しないことを検討してください。     

## <a name="remove-a-visual-from-the-phone-layout"></a>電話レイアウトからのビジュアルの削除
* ビジュアルを削除するには、電話キャンバス上のビジュアルの右上にある [X] をクリックするか、またはビジュアルを選択して、**Delete** キーを押します。
  
   このビジュアルの削除では、電話レイアウト キャンバスからビジュアルが削除されるだけです。 ビジュアルとレポートは影響を受けません。
  
   ![ビジュアルの削除](media/desktop-create-phone-report/desktop-create-phone-report-7.gif)

## <a name="enhance-slicers-to-work-well-in-phone-reports"></a>電話レポートで適切に機能するようにスライサーを拡張する
スライサーは、レポート データのキャンバス上のフィルター処理を行います。 通常のレポートの作成モードでスライサーを設計する場合、電話レポートそれらを使いやすくするために、いくつかのスライサー設定を変更できます。

* レポートの閲覧者が、1 つだけの項目を選択できるか、または複数選択できるかを決定します。
* レポートをスキャンしやすくなるように、スライサーの周りにボックスを配置します。
* スライサーを垂直、水平、または*レスポンシブ*にします。 

スライサーをレスポンシブにすると、スライサーのサイズとシェイプの変更に応じて表示されるオプションの数が増減します。 高さを変えたり、幅を変えたりできます。 非常に小さくすると、レポート ページにフィルターのアイコンだけが表示されるようになります。 

![Power BI のレスポンシブ スライサー](media/desktop-create-phone-report/desktop-create-phone-report-8.png)

詳細については、[レスポンシブ スライサーの作成](power-bi-slicer-filter-responsive.md)に関するページをお読みください。

## <a name="publish-a-phone-report"></a>電話レポートの発行
* レポートの電話バージョンを発行するには、[Power BI Desktop から Power BI サービスにメイン レポートを発行](desktop-upload-desktop-files.md)し、同時に電話バージョンを発行します。
  
    詳しくは、[Power BI での共有およびアクセス許可](service-how-to-collaborate-distribute-dashboards-reports.md)に関するページを参照してください。

## <a name="view-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>スマートフォンまたはタブレット上で最適化されたレポートと最適化されていないレポートを表示する
電話のモバイル アプリの Power BI は、最適化された電話レポートと最適化されていない電話レポートを自動的に検出します。 電話用に最適化されたレポートが存在する場合、Power BI の電話アプリは自動的に電話レポート モードでレポートを開きます。

電話用に最適化されたレポートが存在しない場合は、最適化されていない横長ビューでレポートが開きます。  

電話レポートで、電話の向きを横長に変更すると、レポートを最適化しているかどうかに関係なく、元のレポート レイアウトの最適化されていないビューでレポートが開きます。

一部のページのみを最適化している場合、縦長ビューに、レポートを横長で使用できることを示すメッセージが表示されます。

![最適化されていない電話ページ](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

レポート閲覧者は、スマートフォンまたはタブレットを横向きにして、横長モードでページを表示できます。 詳しくは、[縦モード用に最適化された Power BI レポートとの対話](consumer/mobile/mobile-apps-view-phone-report.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順
* [Power BI でダッシュボードの Phone ビューを作成する](service-create-dashboard-mobile-phone-view.md)
* [電話用に最適化された Power BI レポートを表示する](consumer/mobile/mobile-apps-view-phone-report.md)
* [任意のサイズに最適化されるレスポンシブ ビジュアルを作成する](visuals/desktop-create-responsive-visuals.md)
* 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。

