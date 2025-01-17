---
title: Power BI で外部 R IDE を使用する
description: 外部の IDE を起動し、Power BI で使用できます
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: db4b6d4915e97aaee65806b0bca7801bf4ce951e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876229"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>Power BI で外部 R IDE を使用する
**Power BI Desktop** では、外部の R IDE (統合開発環境) を使用して R スクリプトを作成および調整した後、Power BI でそのスクリプトを使用できます。

![](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>外部の R IDE を有効にする
これまで、R スクリプトを作成して実行するには、**Power BI Desktop** の R スクリプト エディターを使用する必要がありました。 このリリースでは、外部の R IDE を **Power BI Desktop** から起動し、R IDE にデータを自動的にインポートして表示できます。 その後は、その外部 R IDE でスクリプトを修正してから、**Power BI Desktop** にスクリプトを貼り付けて、Power BI のビジュアルとレポートを作成できます。

**Power BI Desktop** の 2016年 9 月リリース (2.39.4526.362 バージョン) 以降、使用する R IDE を指定して、それを **Power BI Desktop** 内から自動的に起動させることができます。

### <a name="requirements"></a>要件
この機能を使用するには、ローカル コンピューターに **R IDE** をインストールする必要があります。 **Power BI Desktop** には R エンジンは含まれず、配置もインストールも行われないので、ローカル コンピューターに **R** を別途インストールする必要があります。 次のオプションで、使用する R IDE を選択できます。

* 任意の R IDE をインストールすることができます。それらの多くは、[Revolution Open ダウンロード ページ](https://mran.revolutionanalytics.com/download/)や [CRAN Repository](https://cran.r-project.org/bin/windows/base/) などで、無料で入手できます。
* **Power BI Desktop** は [R Studio](https://www.rstudio.com/) や [*R Tools for Visual Studio*](https://beta.visualstudio.com/vs/rtvs/) エディターを含む **Visual Studio 2015** もサポートしています。
* さまざまな R IDE をインストールし、次のいずれかを実行して、**Power BI Desktop** で **R IDE** を起動させることもできます。
  
  * **.R** ファイルを、**Power BI Desktop** で起動させる外部 IDE に関連付けることができます。
  * **[オプション]** ダイアログの **[R スクリプトのオプション]** セクションから *[その他]* を選択して、**Power BI Desktop** で起動する必要がある .exe を指定できます。 **[オプション]** ダイアログを表示するには、 **[ファイル]、[オプションと設定]、[オプション]** の順に移動します。
    
    ![](media/desktop-r-ide/r-ide_1b.png)

複数の R IDE がインストールされている場合は、 **[オプション]** ダイアログの *[検出された R IDE]* ドロップダウンから選択して、起動する R IDE を指定できます。

既定で、**Power BI Desktop** は、**R Studio** がローカル コンピューターにインストールされている場合、外部 R IDE としてそれを起動します。**R Studio** がインストールされておらず、**R Tools for Visual Studio** を含む **Visual Studio 2015** がある場合は、代わりにそれが起動されます。 どちらの R IDE もインストールされていない場合は、 **.R** ファイルに関連付けられたアプリケーションが起動します。

**.R** ファイルの関連付けが存在しない場合、 **[オプション]** ダイアログの *[優先する R IDE を参照します]* セクションで、カスタム IDE へのパスを指定できます。 **Power BI Desktop** の **R IDE の起動**矢印アイコンの横にある **[設定]** 歯車アイコンを選択して、別の R IDE を起動することもできます。

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>Power BI Desktop から R IDE を起動する
**Power BI Desktop** から R IDE を起動するには、次の手順を実行します。

1. **Power BI Desktop** にデータを読み込みます。
2. **[フィールド]** ウィンドウで使用するフィールドをいくつか選択します。 スクリプトのビジュアルをまだ有効にしていない場合は、有効にするように促されます。
   
   ![](media/desktop-r-ide/r-ide_3.png)
3. スクリプトのビジュアルを有効にすると、 **[視覚化]** ウィンドウで R のビジュアルを選択できます。選択すると、スクリプトの結果を表示できる空白の R のビジュアルが作成されます。 **[R スクリプト エディター]** ウィンドウも表示されます。
   
   ![](media/desktop-r-ide/r-ide_4.png)
4. R スクリプトで使用するフィールドを選択できるようになります。 フィールドを選択すると、選択したフィールドに基づいて **[R スクリプト エディター]** フィールドにスクリプト コードが自動的に作成されます。 **[R スクリプト エディター]** ウィンドウで R スクリプトを直接作成する (または貼り付ける) ことも、ウィンドウを空白のままにすることもできます。
   
   ![](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > R ビジュアルの既定の集計タイプは、 *[集計しない]* です。
   > 
   > 
5. **Power BI Desktop** から R IDE を直接起動できるようになります。 **[R スクリプト エディター]** のタイトル バーの右側にある **[Launch R IDE]** (R IDE を起動) ボタンを選択します (次の図を参照)。
   
   ![](media/desktop-r-ide/r-ide_6.png)
6. 次の図のように、指定した R IDE が Power BI Desktop によって起動されます (この図では、**RStudio** が既定の R IDE です)。
   
   ![](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > スクリプトを実行した後で **Power BI Desktop** からデータをインポートするために、**Power BI Desktop** はスクリプトの最初の 3 行を追加します。
   > 
   > 
7. **Power BI Desktop** の **[R スクリプト エディター]** ウィンドウで作成したスクリプトは、R IDE の 4 行目以降に表示されます。 この状態になれば、R IDE で R スクリプトを作成できます。 R IDE で R スクリプトが完成した後は、それをコピーし、**Power BI Desktop** の **[R スクリプト エディター]** ウィンドウに貼り付けて戻す必要があります。ただし、**Power BI Desktop** が自動的に生成したスクリプトの先頭 3 行は*除外する*必要があります。 スクリプトの先頭の 3 行は、**Power BI Desktop** にコピーしないでください。これらの行は、**Power BI Desktop** から R IDE にデータをインポートするためだけに使用されたものです。

### <a name="known-limitations"></a>既知の制限事項
Power BI Desktop から直接 R IDE を起動するには、いくつかの制限があります。

* R IDE から **Power BI Desktop** へのスクリプトの自動的なエクスポートはサポートされていません。
* **R クライアント** エディター (RGui.exe) は、エディター自体がファイルを開く機能をサポートしていないため、サポートされていません。

## <a name="next-steps"></a>次の手順
Power BI での R については、次の追加情報を参照してください。

* [Power BI Desktop での R スクリプトの実行](desktop-r-scripts.md)
* [R を使用した Power BI ビジュアルの作成](desktop-r-visuals.md)

