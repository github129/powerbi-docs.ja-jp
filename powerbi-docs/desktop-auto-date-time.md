---
title: Power BI Desktop の自動の日付/時刻
description: Power BI Desktop の自動の日付/時刻機能について説明します。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 7453854376923fbb55376182a8674e5f3d7d1b63
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878778"
---
# <a name="auto-datetime-in-power-bi-desktop"></a>Power BI Desktop の自動の日付/時刻

この記事では、Power BI Desktop でインポート モデルまたは複合モデルを開発しているデータ モデラーを対象としています。

## <a name="background"></a>背景

"_自動の日付/時刻_" は、Power BI Desktop のデータ読み込みオプションです。 このオプションの目的は、モデルに読み込まれた日付列に基づく便利なタイム インテリジェンス レポートをサポートすることです。 具体的には、レポート作成者は、カレンダーの期間を使用してフィルター処理、グループ化、ドリルダウンを行うことができ、モデラーがそれらを明示的に開発する必要はありません。 カレンダーの期間には、年、四半期、月、日が含まれます。

このオプションを有効にすると、次の条件がすべて満たされていれば、Power BI Desktop によって各日付列に対して非表示の自動の日付/時刻テーブルが作成されます。

- テーブル ストレージ モードがインポートである
- 列のデータ型が日付または日付/時刻である
- 列がモデル リレーションシップの "多" の側ではない

## <a name="how-it-works"></a>使い方

各自動の日付/時刻テーブルは、実際には、DAX の [CALENDAR](/dax/calendar-function-dax) 関数を使用してデータ行が生成される[計算テーブル](desktop-calculated-tables.md)です。 各テーブルには、次の 6 つの計算列も含まれます: **Day**、**MonthNo**、**Month**、**QuarterNo**、**Quarter**、**Year**。

> [!NOTE]
> 列の名前と値は、[モデル言語](supported-languages-countries-regions.md#choose-the-language-for-the-model-in-power-bi-desktop)に従って変換および書式設定されます。

また、自動の日付/時刻テーブルの **Date** 列とモデルの日付列の間にリレーションシップが作成されます。

自動の日付/時刻テーブルには、モデルの日付列に格納されているすべての日付値を含む完全なカレンダー年が読み込まれます。 たとえば、日付列の最初の値が 2016 年 3 月 20 日で、最新の値が 2019 年 10 月 23 日である場合、テーブルには 1461 行が格納されます。 2016 年から 2019 年までの 4 カレンダー年の各日付が 1 行で表わされています。 モデルが更新されると、各自動の日付/時刻テーブルも更新され、日付列の値が完全に収まる日付が常に含まれるようになります。

自動の日付/時刻テーブルの行を見ることができるとしたら、次のようになります。

![自動の日付/時刻テーブルの行の表示の例。 7 つの列が表示されています: Date、Day、MonthNo、Month、QuarterNo、Quarter、Year。 2019 年 1 月 1 日から 2019 年 1 月 10 日までの日付を示す 10 行のデータが表示されています。](media/desktop-auto-date-time/auto-date-time-hidden-table-example-rows.png)

> [!NOTE]
> 自動の日付/時刻テーブルは、モデラーからも完全に非表示になります。 **[フィールド]** ペインまたはモデル ビュー ダイアグラムで表示することはできず、その行は [データ] ビューに表示できません。 また、テーブルとその列を、DAX 式で直接参照することはできません。

また、テーブルでは階層も定義されており、年、四半期、月、日の各レベルを経るドリルダウン パスがビジュアルに提供されます。

モデル ビュー ダイアグラムで自動の日付/時刻テーブルを表示できるとしたら、次のようになります (関連する列が強調して示されています)。

![非表示の自動の日付/時刻テーブルの表示の例。 2 つのテーブルが表示されています: Sales および LocalDateTime テーブル。 テーブルは、Sales テーブルの OrderDate 列と LocalDateTime テーブルの Date 列で関連付けられています。 LocalDateTime では、7 つの列が定義されています: Date、Day、Month、MonthNo、Quarter、QuarterNo、Year。また、1 つの階層が定義されています。 階層の名前は Date Hierarchy で、4 つのレベルで構成されています: Year、Quarter、Month、Day。](media/desktop-auto-date-time/auto-date-time-hidden-table-example-diagram.png)

## <a name="work-with-auto-datetime"></a>自動の日付/時刻を使用する

日付列に対して自動の日付/時刻テーブルが存在する場合 (そして、その列が表示されている場合)、レポート作成者に対してその列は **[フィールド]** ペインのフィールドとしては表示されません。 代わりに、日付列の名前を持つ展開可能なオブジェクトとして表示されます。 カレンダー アイコンが前に付いているので、簡単に識別できます。 レポート作成者がそのカレンダー オブジェクトを展開すると、**Date Hierarchy** という名前の階層が表示されます。 階層を展開すると、次の 4 つのレベルが表示されます: **Year**、**Quarter**、**Month**、**Day**。

![Sales テーブルが展開されている [フィールド] ペインの例。 前にカレンダー アイコンの付いた OrderDate フィールドが含まれます。 展開して開かれており、Date Hierarchy という名前の階層が含まれています。 それも展開されており、4 つのレベルが含まれます: Year、Quarter、Month、Day。](media/desktop-auto-date-time/auto-date-time-fields-pane-example.png)

自動の日付/時刻で生成される階層を使用すると、通常の階層とまったく同じ方法でビジュアルを構成できます。 **Date Hierarchy** 階層全体を使用して、または階層の特定のレベルを使用して、ビジュアルを構成できます。

ただし、通常の階層ではサポートされていない機能が 1 つ追加されています。 自動の日付/時刻の階層または階層のレベルがビジュアル ウェルに追加されていると、レポート作成者は、階層の使用と日付列の使用を切り替えることができます。 この方法は、階層とそのレベルではなく日付列のみが必要なビジュアルの場合に役に立ちます。 最初にビジュアルのフィールドを構成し (ビジュアルのフィールドを右クリックするか、下向き矢印をクリック)、次にコンテキスト メニューを使用して、日付列または日付階層に切り替えます。

![OrderDate 階層に対するビジュアルのフィールドの構成例。 開いているコンテキスト メニューに表示されている 2 つのオプションで、OrderDate 列または Date Hierarchy に切り替えることができます。](media/desktop-auto-date-time/auto-date-time-configure-visuals-fields.png)

最後に、DAX で記述されたモデルの計算では、日付列を直接参照することも、非表示の自動の日付/時刻テーブルの列を間接的に参照することもできます。

Power BI Desktop で記述された数式では、通常の方法で日付列を参照できます。 一方、自動の日付/時刻テーブルの列は、特殊な拡張構文を使用して参照する必要があります。 最初に日付列を参照し、その後にピリオド (.) を入力します。 数式バーのオート コンプリートによって、自動の日付/時刻テーブルの列を選択できます。

![数式バーに DAX メジャー式を入力する例。 式は、"Date Count = COUNT(Sales[OrderDate]." まで入力されており、 オート コンプリートの一覧に非表示の自動の日付/時刻テーブルの 7 つの列がすべて表示されています。 それらは次の列です: Date、Day、Month、MonthNo、Quarter、QuarterNo、Year。](media/desktop-auto-date-time/auto-date-time-dax-auto-complete.png)

Power BI Desktop で、有効なメジャー式は次のようになります。

```dax
Date Count = COUNT(Sales[OrderDate].[Date])
```

> [!NOTE]
> このメジャー式は Power BI Desktop では有効ですが、正しい DAX 構文ではありません。 内部的には、Power BI Desktop によって、実際の (非表示の) 自動の日付/時刻テーブルの列が参照されるように、式が入れ替えられます。

## <a name="configure-auto-datetime-option"></a>自動の日付/時刻オプションを構成する

自動の日付/時刻は、"_グローバル_" に、または "_現在のファイル_" 向けに、構成できます。 グローバル オプションは新しい Power BI Desktop ファイルに適用され、いつでも有効または無効にすることができます。 Power BI Desktop の新規インストールでは、両方のオプションが既定でオンに設定されます。

現在のファイルのオプションも、いつでも有効または無効にすることができます。 有効にすると、自動の日付/時刻テーブルが作成されます。 オフにすると、自動の日付/時刻テーブルはモデルからすべて削除されます。

> [!CAUTION]
> 現在のファイル オプションをオフにすると、自動の日付/時刻テーブルが削除されるため、注意が必要です。 それらを使用するように構成されていて破損したレポート フィルターやビジュアルを必ず修正してください。

Power BI Desktop で、 _[ファイル] > [オプションと設定] > [オプション]_ の順に選択し、 **[グローバル]** ページまたは **[現在のファイル]** ページを選択します。 どちらのページでも、オプションは **[タイム インテリジェンス]** セクションにあります。

![Power BI Desktop のオプションの構成。 [グローバル] グループの [データの読み込み] ページが選択されています。 [タイム インテリジェンス] セクションで、[新しいファイルの自動の日付/時刻] オプションがオンになっています。](media/desktop-auto-date-time/auto-date-time-configure-global-options.png)

## <a name="next-steps"></a>次の手順

自動の日付/時刻および関連トピックについて詳しくは、次のリソースを参照してください。

- [Power BI Desktop で日付テーブルを設定し、使用する](desktop-date-tables.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
