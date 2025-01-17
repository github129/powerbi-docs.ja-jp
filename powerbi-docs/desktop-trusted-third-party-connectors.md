---
title: Power BI の信頼されたサードパーティ製コネクタ
description: Power BI で署名付きのサードパーティ製コネクタを信頼する方法
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: ac3f795d6a80d5f143daf68436f41f5771b3c2bb
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876161"
---
# <a name="trusting-third-party-connectors"></a>サードパーティ製コネクタを信頼する

## <a name="why-do-you-need-trusted-third-party-connectors"></a>信頼されたサードパーティ製コネクタが必要な理由

Power BI では、一般に、"データ拡張機能のセキュリティ" レベルをより高いレベルに維持して、Microsoft によって認定されていないコードが読み込まれないようにすることをお勧めします。 ただし、自分で作成したコネクタや、Microsoft 認定パス外でコンサルタントやベンダーから提供されたコネクタなど、特定のコネクタを読み込むことが必要になる場合もあります。

特定のコネクタの開発者は、証明書を使用してコネクタに署名し、セキュリティ設定を引き下げることなく安全に読み込むために必要な情報を提供できます。

セキュリティ設定の詳細については、[こちら](https://docs.microsoft.com/power-bi/desktop-connector-extensibility)を参照してください。

## <a name="using-the-registry-to-trust-third-party-connectors"></a>レジストリを使用してサードパーティ製コネクタを信頼する

Power BI でサードパーティ製コネクタを信頼するには、信頼する証明書の拇印を指定されたレジストリ値内に列記します。 読み込むコネクタの証明書の拇印とこの拇印が一致すれば、Power BI の "推奨" セキュリティ レベルで読み込むことができます。 

レジストリ パスは、HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop です。 パスが存在することを確認するか、パスを作成します。 この場所は、主に IT ポリシーによって制御されていること、および編集するためにローカル コンピューター管理アクセスが必要であることが理由で選択されています。 

![信頼されたサードパーティ キーが設定されていない Power BI Desktop レジストリ](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

上で指定したパスの下に新しい値を追加します。 型は "複数行文字列値" (REG_MULTI_SZ) にする必要があり、"TrustedCertificateThumbprints" という名前にする必要があります。 

![Power BI Desktop レジストリの、キーがない信頼されたサードパーティ製コネクタのエントリ](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

信頼する証明書の拇印を追加します。 複数の証明書を追加するには、区切り記号として "\0" を使用するか、レジストリ エディターで右クリックして [修正] を選択し、各拇印を新しい行に配置します。 サンプルの拇印は、自己署名証明書から取得されます。 

 ![信頼されたサードパーティ キーが設定された Power BI Desktop レジストリ](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

手順に従って作業し、開発者から適切な拇印が提供されている場合、関連付けられている証明書で署名されたコネクタを安全に信頼できるようになります。

## <a name="how-to-sign-connectors"></a>コネクタに署名する方法

自分または開発者が署名する必要があるコネクタがある場合は、[こちら](https://docs.microsoft.com/power-query/handlingconnectorsigning)の Power Query ドキュメントを参照してください。
