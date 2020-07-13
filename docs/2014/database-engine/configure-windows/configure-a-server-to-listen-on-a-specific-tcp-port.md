---
title: 特定の TCP ポートでリッスンするようにサーバーを構成する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfe8a35e9ba0a23edb3fc08833ab015ddbd2f119
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935833"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a>特定の TCP ポートで受信待ちするようにサーバーを構成する方法 (SQL Server 構成マネージャー)
  このトピックでは、SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスが特定の固定ポートで受信待ちするように構成する方法について説明します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の既定のインスタンスは、有効であれば TCP ポート 1433 で受信待ちします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] と [!INCLUDE[ssEW](../../includes/ssew-md.md)] の名前付きインスタンスは、動的ポートを使用するように構成されています。 つまり、これらのインスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの開始時に、使用可能なポートが選択されます。 名前付きインスタンスにファイアウォール経由で接続する場合は、特定のポートで受信待ちするように [!INCLUDE[ssDE](../../includes/ssde-md.md)] を構成します。これにより、ファイアウォールで適切なポートを開くことができます。  
  
 Windows ファイアウォールの既定の設定の詳細と、データベース エンジン、Analysis Services、Reporting Services、および Integration Services に影響する TCP ポートの説明については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」をご覧ください。  
  
> [!TIP]  
>  ポート番号を選択する場合は、 [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) 特定のアプリケーションに割り当てられているポート番号の一覧を確認してください。 未割り当てのポート番号を選択してください。 詳細については、「 [Windows Vista および Windows Server 2008 では TCP/IP の既定の動的ポート範囲が変更されている](https://support.microsoft.com/kb/929851)」を参照してください。  
  
> [!WARNING]  
>  データベース エンジンは、再起動時に新しいポート上でリッスンを開始します。 ただし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは、レジストリを監視し、データベース エンジンが使用していない可能性があっても、構成が変更されるとすぐに新しいポート番号をレポートします。 一貫性を確保し、接続エラーを避けるために、データベース エンジンを再開します。  
  
 **このトピックの内容**  
  
-   **サーバーが特定の TCP ポートで受信待ちするよう構成する方法:**  
  
     [SQL Server 構成マネージャー](#SSMSProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a>SQL Server データベース エンジンに TCP/IP ポート番号を割り当てるには  
  
1.  SQL Server 構成マネージャーのコンソールウィンドウで、[ **SQL Server ネットワークの構成**]、[ ** \<instance name> のプロトコル**] の順に展開し、[ **tcp/ip**] をダブルクリックします。  
  
2.  **[TCP/IP のプロパティ]** ダイアログ ボックスの **[IP アドレス]** タブに、 **IP1**、 **IP2**という形式で **IPAll**まで IP アドレスが表示されます。 このうちいずれかが、ループバック アダプターの IP アドレス 127.0.0.1 です。 追加の IP アドレスがコンピューターの各 IP アドレスとして表示されます。 各アドレスを右クリックし、**[プロパティ]** をクリックして、構成する IP アドレスを識別します。  
  
3.  **[TCP 動的ポート]** ダイアログ ボックスには、 **が動的ポートで受信待ちすることを示す**0 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が表示されています。この 0 を削除します。  
  
4.  [**IP**_n_ **のプロパティ**] ボックスの **[TCP ポート]** ボックスに、この IP アドレスが受信待ちするポート番号を入力し、**[OK]** をクリックします。  
  
5.  コンソール ペインで、**[SQL Server のサービス]** をクリックします。  
  
6.  詳細ウィンドウで**SQL Server (**) を右クリックし、 \<instance name> **)** [**再起動**] をクリックしてを停止して再起動し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
 特定のポートで受信待ちするように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を構成した後、次の 3 つの方法でクライアント アプリケーションを使用して特定のポートに接続できます。  
  
-   サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行し、名前を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続する。  
  
-   ポート番号を指定してクライアント上に別名を作成する。  
  
-   クライアントで、カスタム接続文字列を使用して接続するように指定します。  
  
## <a name="see-also"></a>参照  
 [クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
