---
title: Microsoft Power BI Premium 容量のシナリオ
description: Microsoft Power BI Premium 容量の一般的なシナリオについて説明します。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 3190645044c930c1c63fd7c199883d784723d6f0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881254"
---
# <a name="premium-capacity-scenarios"></a>Premium 容量のシナリオ

この記事では、Power BI premium 容量が実装されている実際のシナリオについて説明します。 一般的な問題と課題、および問題を特定して解決する方法についても説明します。

- [データセットを最新の状態に保つ](#keeping-datasets-up-to-date)
- [応答の遅いデータセットを識別する](#identifying-slow-responding-datasets)
- [データセットの応答が散発的に遅くなる原因を特定する](#identifying-causes-for-sporadically-slow-responding-datasets)
- [十分なメモリがあるかどうか確認する](#determining-whether-there-is-enough-memory)
- [十分な CPU があるかどうか確認する](#determining-whether-there-is-enough-cpu)

手順およびグラフとテーブルの例は、Power BI 管理者がアクセスできる **Power BI Premium Capacity Metrics アプリ**からのものです。

## <a name="keeping-datasets-up-to-date"></a>データセットを最新の状態に保つ

このシナリオでは、レポートのデータが古いように見えることがあるというユーザーからの苦情があって、調査が開始されました。

管理者は、アプリで **[Refreshes]\(更新\)** ビジュアルを操作し、 **[Max Wait Time]\(最大待機時間\)** 統計情報の降順でデータセットを並べ替えます。 このビジュアルは、待機時間が最も長いデータセットを明らかにするのに役立ちます。データセットは、ワークスペース名別にグループ化されています。

![ワークスペース別にグループ化され、最大待機時間の降順で並べ替えられているデータセットの更新](media/service-premium-capacity-scenarios/dataset-refreshes.png)

**[Hourly Average Refresh Wait Times]\(時間単位での平均更新待機時間\)** ビジュアルでは、更新の待機時間のピークが毎日常に午後 4 時前後であることがわかります。

![午後 4 時に定期的にピークになる更新待機](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

このような結果に対しては、いくつかの説明が考えられます。

- 同時に発生する更新の試行が多すぎて、容量ノードで定義されている制限を超えている可能性があります。 この場合は、既定のメモリ割り当てを使用する P1 で、更新が同時に 6 回行われています。

- 更新対象のデータセットが大きすぎて、使用可能なメモリに収まりきらない可能性があります (完全な更新には、少なくとも 2 倍のメモリが必要です)。
- Power Query のロジックが非効率的なため、データセットの更新中にメモリ使用量が急増している可能性があります。 ビジー状態の容量では、この急増が物理的な制限に達し、更新が失敗して、容量での他のレポート表示操作に影響している可能性があります。
- 使用可能なメモリが限られているため、メモリに常駐する必要のある頻繁にクエリされるデータセットにより、他のデータセットの更新機能が影響を受けている可能性があります。

Power BI 管理者は、次の状態を探して調査に役立てることができます。

- 使用可能なメモリが更新対象のデータセットのサイズの 2 倍未満の場合に、データ更新時に使用可能なメモリの不足。
- 更新前に更新が行われてないためにメモリ内に存在しない状態で、更新量が多いときに対話型トラフィックの表示を開始したデータセット。 Power BI 管理者は、アプリの **[Datasets]\(データセット\)** タブのデータセット領域を見ることで、任意の時点でメモリに読み込まれているデータセットを確認できます。 その後、管理者は、 **[Hourly Loaded Dataset Counts]\(時間単位での読み込まれたデータセット数\)** でいずれかのバーをクリックすることにより、特定の時刻でクロスフィルターを適用できます。 次の図に表示されている一時的な急増は、複数のデータセットがメモリに読み込まれた時刻を示します。これにより、スケジュールされた更新の開始が遅れる可能性があります。
- スケジュールされているデータ更新開始時における、データセットの削除数の増加。 このような削除は、更新の前に提供された異なる対話型レポートが多すぎるため、メモリ不足が発生したことを示している可能性があります。 **[Hourly Dataset Evictions and Memory Consumption]\(時間単位でのデータセット削除数とメモリ消費量\)** ビジュアルで、削除の急増が明確に示されている場合があります。

次の図では、読み込まれたデータセット数の一時的な急増が示されており、これは対話型クエリにより更新の開始が遅れたことを意味します。 **[Hourly Loaded Dataset Counts]\(時間単位での読み込まれたデータセット数\)** ビジュアルで期間を選択すると、 **[Dataset Sizes]\(データセット サイズ\)** ビジュアルがクロスフィルター処理されます。

![読み込まれたデータセット数の一時的な急増は、対話型クエリにより更新の開始が遅れたことを示す](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

Power BI 管理者は、次のようにして、データ更新を開始するのに十分なメモリを確保するための手順を実行することで、問題の解決を試みることができます。

- データセットの所有者に連絡して、データ更新スケジュールを調整し、間隔を空けて行うよう依頼します。
- 不要なダッシュボードやダッシュボード タイル (特に、行レベルのセキュリティを適用するもの) を削除することによって、データセットのクエリの負荷を軽減します。
- Power Query のロジックを最適化することで、データ更新を高速化します。 計算列またはテーブルのモデリングを改善します。 データセットのサイズを小さくするか、データの増分更新を実行するように大きなデータセットを構成します。

## <a name="identifying-slow-responding-datasets"></a>応答の遅いデータセットを識別する

このシナリオでは、ユーザーから特定のレポートを開くのに時間がかかり、ハングすることもあるという苦情があって、調査が開始されました。

Power BI 管理者は、アプリの **[Query Durations]\(クエリ所要時間\)** ビジュアルを使用し、 **[Average Duration]\(平均所要時間\)** の降順にデータセットを並べ替えることによって、パフォーマンスが最も悪いデータセットを確認できます。 また、このビジュアルではデータセットのクエリ数も示されるため、データセットのクエリ頻度を確認できます。

![パフォーマンスが最も悪いデータセット](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

管理者は、 **[Query Duration Distribution]\(クエリ所要時間の分布\)** ビジュアルを参照できます。このビジュアルでは、フィルター処理された期間に対する、バケット化クエリ パフォーマンス (30 ミリ秒未満、0 - 100 ミリ秒) の全体的な分布が示されます。 一般に、かかる時間が 1 秒以下のクエリは、ほとんどのユーザーが応答していると見なします。クエリの時間が長くなるほど、パフォーマンスが悪いという認識が増加する傾向があります。

**[Hourly Query Duration Distribution]\(時間単位でのクエリ所要時間の分布\)** ビジュアルを使用すると、Power BI 管理者は、容量のパフォーマンスが低下していると認識される可能性がある時間帯を特定できます。 所要時間が 1 秒を超えるクエリを表す棒のセグメントが大きいほど、ユーザーが低パフォーマンスと認識する可能性が高くなります。

ビジュアルは対話型であり、棒のセグメントを選択すると、レポート ページの対応する **[Query Durations]\(クエリ所要時間\)** テーブル ビジュアルがクロスフィルター処理されて、それが表すデータセットが示されます。 このクロスフィルター処理により、Power BI 管理者は、応答速度の遅いデータセットを簡単に識別できます。

次の図では、 **[Hourly Query Duration Distributions]\(時間単位でのクエリ所要時間の分布\)** によってフィルター処理されたビジュアルの、1 時間のバケットでパフォーマンスが最も悪いデータセットの部分が示されています。 

![フィルター処理された [Hourly Query Duration Distributions]\(時間単位でのクエリ所要時間の分布\) ビジュアルで、パフォーマンスの悪いデータセットが示されている](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

特定の 1 時間についてパフォーマンスの悪いデータセットが特定されたら、Power BI 管理者は、パフォーマンスの低下が容量の過負荷によるものか、それともデータセットまたはレポートの設計がよくないためかを、調べることができます。 **[Query Wait Times]\(クエリ待機時間\)** ビジュアルを参照し、平均クエリ待機時間の降順でデータセットを並べ替えることができます。 クエリの大きな割合が待機している場合、そのデータセットに対する要求の多さが、クエリの待機が多くなる原因であると考えられます。 クエリの平均待機時間がかなり長い (100 ミリ秒超) 場合は、データセットとレポートを調べて、最適化できるかどうかを確認します。 たとえば、特定のレポート ページのビジュアルを減らしたり、DAX 式を最適化したりします。

![[Query Wait Times]\(クエリ待機時間\) ビジュアルは、パフォーマンスの低いデータセットを明らかにするのに役立つ](media/service-premium-capacity-scenarios/query-wait-times.png)

データセットでクエリ待機時間が長くなる場合は、いくつかの理由が考えられます。

- 最適ではないモデルの設計、メジャー式、またはレポートの設計 - 多くの CPU を消費する実行時間の長いクエリに寄与する可能性のあるすべての状況。 これにより、CPU スレッドが使用可能になるまで新しいクエリは待機させられ、営業時間のピーク時によく見られる、コンボイ効果 (交通渋滞を考えてください) が発生する可能性があります。 **[Query Waits]\(クエリ待機\)** ページが、データセットの平均クエリ待機時間が長いかどうかを判断するための主要なリソースです。
- 同じレポートまたはデータセットを使用している、多数の同時容量ユーザー (数百から数千)。 データセットが適切に設計されていても、コンカレンシーしきい値を超えるとパフォーマンスが低下する可能性があります。 これは通常、1 つのデータセットのクエリ数の値が他のデータセットに比べて極端に高くなることで示されます (たとえば、1 つのデータセットに対するクエリが 30 万件であるのに対し、他のすべてのデータセットに対するクエリは 3 万件未満)。 ある時点で、このデータセットを待機するクエリは調整され始め、これは **[Query Durations]\(クエリ所要時間\)** ビジュアルで確認できます。
- 多くの異なるデータセットに対して同時にクエリが実行され、データセットがメモリに頻繁に出入りしたことによるスラッシング。 これにより、データセットがメモリに読み込まれるときのパフォーマンスが低下します。 Power BI 管理者は、 **[Hourly Dataset Evictions and Memory Consumption]\(時間単位でのデータセット削除およびメモリ消費量\)** ビジュアルを参照して確認できます。このビジュアルで、メモリに読み込まれた多数のデータセットが繰り返し削除されていることが示されている可能性があります。

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>データセットの応答が散発的に遅くなる原因を特定する

このシナリオでは、ときどきレポートのビジュアルの応答が遅くなったり、応答しなくなることがあるが、それ以外のときは許容できる応答性であることをユーザーが説明したことで、調査が開始されました。

次のように、アプリの **[Query Durations]\(クエリ所要時間\)** セクションを使用して、原因となるデータセットを探しました。

- 管理者は、 **[Query Durations]\(クエリ所要時間\)** ビジュアルで、データセット別にデータセットをフィルター処理し (クエリが実行されている上位のデータセットから開始)、 **[Hourly Query Distributions]\(時間単位でのクエリの分布\)** ビジュアルでクロスフィルター処理されたバーを調べました。
- 1 つの 1 時間の棒が、そのデータセットの他の 1 時間の棒と比べて、すべてのクエリ期間グループに対して高い変化率を示している場合 (色の比率が急激に変化している場合など)、このデータセットは、このデータセットが散発的なパフォーマンスの変化を示したことを意味します。
- 不規則なクエリ パフォーマンス低下の部分を示す 1 時間の棒は、そのデータセットが、他のデータセットのアクティビティによって発生したノイズの多い近隣効果によって影響を受けた期間を示していました。

次の図では、"(3,10s]" 実行時間バケットのサイズによって示される、データセットのパフォーマンスの大きな低下が発生した、1 月 30 日の 1 時間が示されています。 その 1 時間の棒をクリックすると、その間にメモリに読み込まれたすべてのデータセットが表示され、ノイズの多い近隣効果の原因になった可能性のあるデータセットがわかります。

![パフォーマンスの低下を示す棒 (拡大部分)](media/service-premium-capacity-scenarios/worst-performing-queries.png)

問題のある期間を特定した後 (たとえば、上の図の 1 月 30 日)、Power BI 管理者は、すべてのデータセット フィルターを削除してから、その期間だけでフィルター処理して、この期間中にアクティブにクエリが実行されたデータセットを特定できます。 通常、ノイズの多い近隣効果の原因になるデータセットは、クエリ回数が最も多いデータセット、または平均クエリ所要時間が最も長いデータセットです。

この問題を解決するには、原因のデータセットを異なる Premium 容量の異なるワークスペースに分散させるか、または、データセットのサイズ、消費要件、データ更新のパターンがサポートされている場合は、共有容量に分散させます。

逆が当てはまる場合もあります。 Power BI 管理者は、データセットのクエリのパフォーマンスが劇的に向上した期間を特定し、存在しなくなったものを探します。 その時点で特定の情報が欠落している場合は、それが原因となっている問題の特定に役立つ可能性があります。

## <a name="determining-whether-there-is-enough-memory"></a>十分なメモリがあるかどうか確認する

容量がワークロードを完了するのに十分なメモリがあるかどうかを判断するには、Power BI 管理者は、アプリの **[Datasets]\(データセット\)** タブの **[Consumed Memory Percentages]\(消費されたメモリの割合\)** ビジュアルを参照できます。 **[All]\(すべて\)** (合計) のメモリは、アクティブにクエリまたは処理が実行されているかどうかに関係なく、メモリに読み込まれたデータセットによって消費されたメモリを表します。 **[Active]\(アクティブ\)** のメモリは、アクティブに処理されているデータセットによって消費されたメモリを表します。

正常な容量では、ビジュアルは次のようになり、すべて (合計) のメモリとアクティブなメモリの間にギャップがあることが示されています。

![正常な容量では、すべて (合計) のメモリとアクティブなメモリの間にギャップが示される](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

メモリ不足が発生している容量では、同じビジュアルでアクティブなメモリと合計メモリの収束が明確に示されます。つまり、追加のデータセットをメモリに読み込むことができません。 この場合、Power BI 管理者は、 **[容量の再起動]** をクリックできます (管理ポータルの容量設定領域にある **[詳細設定オプション]** 内)。 容量を再起動すると、すべてのデータセットがメモリからフラッシュされ、必要に応じて (クエリまたはデータ更新により) メモリに再度読み込めるようになります。

![**アクティブ**なメモリと**すべて**のメモリの収束](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>十分な CPU があるかどうか確認する

一般に、容量の平均 CPU 使用率は 80% 未満に留まっている必要があります。 この値を超えると、容量が CPU の飽和に近づいていることを意味します。

CPU が飽和すると、すべての操作を処理しようとして容量で多くの CPU コンテキスト切り替えが実行されるため、必要以上に操作に時間がかかるようになります。 同時実行クエリの数が多い Premium 容量では、これは長いクエリ待機時間によって示されます。 クエリの待機時間が長いと、通常より応答速度が低下します。 Power BI 管理者は、 **[Hourly Query Wait Time Distributions]\(時間単位のクエリ待機時間の分布\)** ビジュアルを見ることによって、CPU が飽和状態になっていることを簡単に特定できます。 定期的に発生するクエリ待機時間カウントのピークは、潜在的な CPU 飽和を示します。

![定期的に発生するクエリ待機時間カウントのピークは潜在的な CPU 飽和を示します](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

バックグラウンド操作が CPU 飽和の原因になっている場合、バックグラウンド操作でも同様のパターンが検出されることがあります。 Power BI 管理者は、特定のデータセットに対する更新時間の断続的な急増を探すことができます。これは、その時点での CPU の飽和を示す可能性があります (おそらく、他の実行中のデータセット更新や対話型クエリなどのため)。 この場合、アプリの **[System]\(システム\)** ビューを参照しても、CPU が 100% になっているとは限りません。 **[System]\(システム\)** ビューには 1 時間ごとの平均が表示されますが、CPU は数分間の大量の操作に対して飽和状態になることがあり、これは待機時間の急上昇として示されます。

CPU の飽和の影響を確認するには、さらに微妙な違いがあります。 待機しているクエリの数は重要ですが、はっきりとパフォーマンスが低下することはなくても、クエリの待機時間は、常に一定の程度発生します。 データセットの中には、他のデータセットより CPU の飽和の影響を受けやすいものがあります (複雑さやサイズを示す、長い平均クエリ時間)。 Power BI 管理者は、 **[Hourly Wait Time Distribution]\(時間単位の待機時間の分布\)** ビジュアルにおける棒の色の構成の変化を調べることで、このようなデータセットを簡単に識別できます。 異常な棒を見つけた後は、その期間中にクエリが待機していたデータセットを検索し、クエリの平均所要時間と比較してクエリの平均待機時間を調べることができます。 この 2 つのメトリックが同程度で、データセットのクエリのワークロードが重要でない場合、データセットが CPU の不足によって影響を受ける可能性があります。

この効果は、複数のユーザーによる (たとえば、トレーニング セッションでの) 高頻度のクエリの短時間の急増でデータセットが消費される場合に特に顕著です。その結果、急増のたびに CPU の飽和が発生します。 この場合、このデータセットでのクエリの待機時間が大幅に長くなり、容量内の他のデータセットにも影響する可能性があります (ノイズの多い近隣効果)。

場合によっては、Power BI 管理者は、データセットの所有者に対し、レポートではなく、ダッシュボード (キャッシュされたタイルのデータセットの更新で、定期的にクエリが実行されます) を作成することで、揮発性の低いクエリ ワークロードにするよう要求できます。 これは、ダッシュボードが読み込まれるときのスパイクを防ぐのに役立ちます。 このソリューションは、特定のビジネス要件に対して常に可能であるとは限りませんが、データセットを変更することなく、CPU の飽和を回避する効果的な方法になる可能性があります。

## <a name="acknowledgements"></a>謝辞

この記事は、データ プラットフォーム MVP であり、[Bitwise Solutions](https://www.bitwisesolutions.com.au/) の独立 BI 専門家である Peter Myers によって執筆されました。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [アプリで Premium 容量を監視する](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [管理ポータルで容量を監視する](service-admin-premium-monitor-portal.md)   

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

||||||