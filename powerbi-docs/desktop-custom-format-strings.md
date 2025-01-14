---
title: Power BI Desktop でカスタム書式設定文字列を使用する
description: Power BI Desktop で書式設定文字列をカスタマイズする方法を説明します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1c1f049f8ba8c7808001b8566b1d10424a1b2ed1
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878346"
---
# <a name="use-custom-format-strings-in-power-bi-desktop"></a>Power BI Desktop でカスタム書式設定文字列を使用する

**Power BI Desktop** でカスタム書式設定文字列を使用すると、ビジュアルでのフィールドの表示方法をカスタマイズし、意図したとおりにレポートが表示されるようにすることができます。

![カスタム書式設定文字列の使用](media/desktop-custom-format-strings/custom-format-strings-01.png)


## <a name="how-to-use-custom-format-strings"></a>カスタム書式設定文字列の使用方法

カスタム書式設定文字列を作成するには、 **[モデリング]** ビューでフィールドを選択し、 **[プロパティ]** ウィンドウで **[書式]** を選択します。

![[書式] ドロップダウンから [カスタム]](media/desktop-custom-format-strings/custom-format-strings-02.png)

**[書式]** ドロップダウンから **[カスタム]** を選択すると、よく使用される書式設定文字列の一覧から選択できます。 

![カスタム書式設定文字列の使用](media/desktop-custom-format-strings/custom-format-strings-03.png)


## <a name="supported-custom-format-syntax"></a>サポートされているカスタム書式設定構文

カスタム書式設定文字列は、Excel や他の Microsoft 製品に共通する VBA スタイルの構文に従いますが、他の製品で使用されるすべての構文はサポートされていません。 

次の表では、Power BI でサポートされている構文を定義します。


次の表では、サポートされている**日付記号**を示します。

| **記号** | **範囲** |
| --- | --- |
| _d_ | 1 - 31 (先行ゼロを含まない月の通算日) |
| _dd_ | 01 - 31 (先行ゼロを含む月の通算日) |
| _m_ | 1 - 12 (先行ゼロを含まない月、1 月 = 1) |
| _mm_ | 01 - 12 (先行ゼロを含む月、1 月 = 01) |
| _mmm_ | 月の省略名を表示します (イスラム暦の月の名前には省略形がありません) |
| _mmmm_ | 月の完全な名前を表示します |
| _y_ | 1 - 366 (年の通算日) |
| _yy_ | 00 - 99 (年の最後の 2 桁) |
| _yyyy_ | 100 - 9999 (3 桁または 4 桁の年) |

次の表では、サポートされている**時刻記号**を示します。

| **記号** | **範囲** |
| --- | --- |
| _h_ | 0 - 23 (1 - 12 の場合は &quot;AM&quot; または &quot;PM&quot; を付加します) (時刻、先行ゼロなし) |
| _hh_ | 00 - 23 (01 - 12 の場合は &quot;AM&quot; または &quot;PM&quot; を付加します) (時刻、先行ゼロあり) |
| _n_ | 0 - 59 (分、先行ゼロなし) |
| _nn_ | 00 - 59 (分、先行ゼロあり) |
| _m_ | 0 - 59 (分、先行ゼロなし)。 前に _h_ または _hh_ がある場合のみ |
| _mm_ | 00 - 59 (分、先行ゼロあり)。 前に _h_ または _hh_ がある場合のみ |
| _s_ | 0 - 59 (秒、先行ゼロなし) |
| _ss_ | 00 - 59 (秒、先行ゼロあり) |


カスタム値文字列の書式設定方法の[例](https://docs.microsoft.com/office/vba/language/reference/user-interface-help/format-function-visual-basic-for-applications#example)を参照してください。

ユーザー定義の数値式では、1 から 3 個のセクションをセミコロンで区切って指定できます。 セミコロンの間に何も含まれていない場合、不足しているセクションは表示されません (&quot;&quot; になります)。 セミコロンを指定しないと、正の書式設定が使用されます。

さまざまな値文字列のさまざまな書式設定の例を次に示します。

|   | **書式設定文字列** |   |   |   |
| --- | --- | --- | --- | --- |
| **値** | **0.00;-0.0;&quot;Zero&quot;** | **0.00;;** | **0.00;-0.0;** | **0.00;** |
| **-1.234** | -1.2 | &quot;&quot; | -1.2 | &quot;&quot; |
| **0** | &quot;Zero&quot; | &quot;&quot; | &quot;&quot; | 0.00 |
| **1.234** | 1.23 | 1.23 | 1.23 | 1.23 |

次の表では、定義済みの**名前付きの日付と時刻の書式設定**を示します。

| **書式設定名** | **説明** |
| --- | --- |
| **一般の日付** | 日付や時刻を表示します (例: 4/3/93 05:34 PM)。 小数部分がない場合は、日付のみを表示します (例: 4/3/93)。 整数部分がない場合は、時刻のみを表示します (例: 05:34 PM)。 日付の表示は、システム設定によって決まります。 |
| **長い日付** | システムの長い日付形式に従って日付を表示します。 |
| **短い日付** | システムの短い日付形式を使用して日付を表示します。 |
| **長い時刻** | システムの長い時刻形式を使用して時刻を表示します。時、分、秒が含まれます。 |
| **短い時刻** | 24 時間形式を使用して時刻を表示します (例: 17:45)。 |

名前付きの数値書式設定

次の表では、定義済みの**名前付きの数値の書式設定**を示します。

| **書式設定名** | **説明** |
| --- | --- |
| **一般的な数字** | 桁区切り記号を付けずに数値を表示します。 |
| **通貨** | 必要に応じて、数値を桁区切り記号付きで表示します。小数点区切り記号の右側に 2 桁の数字を表示します。 出力はシステムのロケール設定に基づいきます。 |
| **固定** | 小数点区切り記号の左側に 1 桁以上、右側に 2 桁の数字を表示します。 |
| **標準** | 桁区切り記号付きで、小数点区切り記号の左側に 1 桁以上、右側に 2 桁の数字を表示します。 |
| **パーセント** | 数値に 100 を乗算し、右側にパーセント記号 ( **%** ) を付けて表示します。小数点区切り記号の右側に、常に 2 桁の数字を表示します。 |
| **科学的表記** | 標準的な科学的表記法を使用します。 |



次の表では、**ユーザー定義の日付/時刻書式設定**を作成するために使用できる文字を示します。

| **文字** | **説明** |
| --- | --- |
| ( **:** ) | 時刻の区切り記号。 ロケールによっては、他の文字を使用して時刻区切り記号が表される場合があります。 時刻の値を書式設定するときに、時刻区切り記号で時、分、秒を区切ります。 書式設定された出力で時刻区切り記号として実際に使用される文字は、システム設定によって決まります。 |
| ( **/** ) | 日付の区切り記号。 ロケールによっては、他の文字を使用して日付区切り記号が表される場合があります。 日付の値を書式設定するときに、日付区切り記号で日、月、年を区切ります。 書式設定された出力で日付区切り記号として実際に使用される文字は、システム設定によって決まります。 |
| d | 先頭に 0 を付けずに数値で日を表示します (1 – 31)。 |
| dd | 先頭に 0 を付けて数値で日を表示します (01 – 31)。 |
| ddd | 省略形で曜日を表示します (Sun – Sat)。 ローカライズされます。 |
| dddd | 完全な名前で曜日を表示します (Sunday – Saturday)。 ローカライズされます。 |
| m | 先頭に 0 を付けずに数値で月を表示します (1 – 12)。 m が h または hh の直後にある場合、月ではなく分が表示されます。 |
| mm | 先頭に 0 を付けて数値で月を表示します (01 – 12)。 m が h または hh の直後にある場合、月ではなく分が表示されます。 |
| mmm | 省略形で月を表示します (Jan – Dec)。 ローカライズされます。 |
| mmmm | 完全な月の名前で月を表示します (January – December)。 ローカライズされます。 |
| y | 年の通算日を数値で表示します (1 – 366)。 |
| yy | 年を 2 桁の数字で表示します (00 – 99)。 |
| yyyy | 年を 4 桁の数字で表示します (100 – 9999)。 |
| h | 先頭に 0 を付けずに数値で時刻を表示します (0 – 23)。 |
| hh | 先頭に 0 を付けて数値で時刻を表示します (00 – 23)。 |
| n | 先頭に 0 を付けずに数値で分を表示します (0 – 59)。 |
| nn | 先頭に 0 を付けて数値で分を表示します (00 – 59)。 |
| s | 先頭に 0 を付けずに数値で秒を表示します (0 – 59)。 |
| ss | 先頭に 0 を付けて数値で秒を表示します (00 – 59)。 |
| AM/PM | 12 時間制を使用し、正午より前の時刻には大文字の AM を表示します。正午から午後11:59 までの時刻には、大文字の PM を表示します。 |

次の表では、**ユーザー定義の数値書式設定**を作成するために使用できる文字を示します。

| **文字** | **説明** |
| --- | --- |
| なし | 書式設定なしで数値を表示します。 |
| ( **0** ) | 数字のプレースホルダー。 数字または 0 を表示します。 式の書式設定文字列で 0 が出現する位置に数字がある場合は、それを表示します。それ以外の場合は、その位置に 0 を表示します。 数値の桁数が、書式設定式のゼロ (小数点の両側) の数より少ない場合は、先頭または末尾に 0 が表示されます。 数値の小数点区切り記号より右側の桁数が、書式設定式の小数点区切り記号より右側の 0 の数より多い場合、数値は小数点以下の 0 の数に丸められます。 数値の小数点区切り記号より左側の桁数が、書式設定式の小数点区切り記号より左側の 0 の数より多い場合、余分な数字が変更なしで表示されます。 |
| ( **#** ) | 数字のプレースホルダー。 数字を表示するか、または何も表示しません。 式の書式設定文字列で # が出現する位置に数字がある場合は、それを表示します。それ以外の場合は、その位置に何も表示しません。 この記号は、0 の数字プレースホルダーのように機能します。ただし、数値の桁数が、書式設定式の小数点区切り記号の両側にある # 文字と同じかそれよりも少ない場合、先頭と末尾のゼロは表示されません。 |
| ( **.** ) | 小数点のプレースホルダー。 ロケールによっては、小数点区切り記号としてコンマが使用されます。 小数点プレースホルダーにより、小数点区切り記号の左側と右側に表示される数字の数が決まります。 書式指定式のこの記号の左側に数字記号のみが含まれている場合、1 より小さい数値は小数点区切り記号で始まります。 小数部の前にゼロを表示するには、小数点区切り記号の左側の最初の桁プレースホルダーとして 0 を使用します。 書式設定された出力で、小数点プレースホルダーとして実際に使用される文字は、システムによって認識される数値書式によって異なります。 |
| ( **%)** | パーセント プレースホルダー。 式に 100 が乗算されます。 パーセント文字 ( **%** ) は、書式設定文字列内で出現する位置に挿入されます。 |
| ( **,** ) | 桁区切り記号。 ロケールによっては、桁区切り記号としてピリオドが使用されます。 桁区切り記号は、小数点区切り記号の左側に 4 桁以上ある数値で、千の位と百の位を区切ります。 数字プレースホルダー (**0** または **#** ) で囲まれた桁区切り記号が書式設定に含まれる場合に、桁区切り記号の標準的な使用方法が指定されます。 2 つの隣接する桁区切り記号がある場合、または小数点区切り記号のすぐ左に桁区切り記号がある場合は (小数点が指定されているかどうかにかかわらず)、&quot;必要に応じて、数値が 1000 で除算されて丸められます&quot;。たとえば、書式設定文字列 &quot;##0,,&quot; を使用すると、1 億を 100 として表すことができます。 100 万より小さい数値は 0 と表示されます。 小数点区切り記号のすぐ左側以外の任意の位置にある 2 つの隣接する桁区切り記号は、単に桁区切り記号の使用の指定として処理されます。 書式設定された出力で、桁区切り記号として実際に使用される文字は、システムによって認識される数値書式によって異なります。 |
| ( **:** ) | 時刻の区切り記号。 ロケールによっては、他の文字を使用して時刻区切り記号が表される場合があります。 時刻の値を書式設定するときに、時刻区切り記号で時、分、秒を区切ります。 書式設定された出力で時刻区切り記号として実際に使用される文字は、システム設定によって決まります。 |
| ( **/** ) | 日付の区切り記号。 ロケールによっては、他の文字を使用して日付区切り記号が表される場合があります。 日付の値を書式設定するときに、日付区切り記号で日、月、年を区切ります。 書式設定された出力で日付区切り記号として実際に使用される文字は、システム設定によって決まります。 |
| ( **E- E+ e- e+** ) | 科学的表記形式。 書式設定式で、E-、E+、e-、e+ の右側に少なくとも 1 つの数字プレースホルダー (**0** または **#** ) がある場合、数値は科学的な形式で表示され、E または e が数値とその指数の間に挿入されます。 右側の桁プレースホルダーの数によって、指数部の桁数が決まります。 負の指数の横にマイナス記号を付けるには、E- または e- を使用します。 負の指数の横にマイナス記号を付け、正の指数の横にプラス記号を付けるには、E+ または e+ を使用します。 |
| **- + $**  ( ) | リテラル文字を表示します。 一覧に含まれていない文字を表示するには、その文字の前に円記号 (\) を付けるか、または二重引用符 (&quot; &quot;) で囲みます。 |
| ( * *\** ) | 書式設定文字列内の次の文字を表示します。 リテラル文字として特別な意味を持つ文字を表示するには、その文字の前に円記号 (\) を付けます. 円記号自体は表示されません。 円記号の使用は、次の文字を二重引用符で囲むことと同じです。 円記号を表示するには、2 つの円記号 (\\) を使用します。 リテラル文字として表示できない文字の例としては、日付書式設定と時刻書式設定の文字 (a、c、d、h、m、n、p、q、s、t、w、y、/、:)、数値書式設定の文字 (#、0、%、E、e、コンマ、ピリオド)、文字列書式設定の文字 (@、&amp;、\&lt;、\&gt;、!) があります。 |
| (&quot;ABC&quot;) | 二重引用符 (&quot; &quot;) の内側にある文字列を表示します。 |


## <a name="next-steps"></a>次の手順
次の記事にも興味をもたれるかもしれません。

* [VBA の書式設定文字列](https://docs.microsoft.com/office/vba/language/reference/user-interface-help/format-function-visual-basic-for-applications#example)
* [Power BI Desktop のメジャー](desktop-measures.md)
* [Power BI Desktop でのデータ型](desktop-data-types.md)
* [テーブルでの条件付き書式設定](desktop-conditional-table-formatting.md)

