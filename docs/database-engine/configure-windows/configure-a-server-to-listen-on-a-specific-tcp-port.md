---
title: 特定の TCP ポートで受信待ちするようにサーバーを構成する | Microsoft Docs
description: SQL Server 構成マネージャーを使用して、既定のポート 1433 以外の特定の固定ポートでリッスンするようにデータベース エンジンを構成する方法について説明します。
ms.custom: ''
ms.date: 04/25/2017
ms.prod: sql
ms.prod_service: high-availability
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 15d1d1ab04adb47772706f8b1495b8ddef8b4fa3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789837"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port"></a>特定の TCP ポートで受信待ちするようにサーバーを構成する
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このトピックでは、SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスが特定の固定ポートで受信待ちするように構成する方法について説明します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の既定のインスタンスは、有効であれば TCP ポート 1433 で受信待ちします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] と [!INCLUDE[ssEW](../../includes/ssew-md.md)] の名前付きインスタンスは、 [動的ポート](../../tools/configuration-manager/tcp-ip-properties-ip-addresses-tab.md)を使用するように構成されています。 つまり、これらのインスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの開始時に、使用可能なポートが選択されます。 名前付きインスタンスにファイアウォール経由で接続する場合は、特定のポートで受信待ちするように [!INCLUDE[ssDE](../../includes/ssde-md.md)] を構成します。これにより、ファイアウォールで適切なポートを開くことができます。  

ポート 1433 は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既知の標準であるため、セキュリティを強化するために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のポート番号を変更する必要があると指定されることがあります。 環境によってはそれが役に立つことがあります。 ただし、TCP/IP アーキテクチャでは[ポート スキャナー](https://wikipedia.org/wiki/Port_scanner)で開いているポートをクエリすることが許可されているため、ポート番号の変更は堅牢なセキュリティ対策とは見なされません。

 Windows ファイアウォールの既定の設定の詳細と、データベース エンジン、Analysis Services、Reporting Services、および Integration Services に影響する TCP ポートの説明については、「 [SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」をご覧ください。  
  
> [!TIP]  
>  ポート番号を選択する際は、特定のアプリケーションに割り当てられているポート番号の一覧を [https://www.iana.org/assignments/port-numbers](https://www.iana.org/assignments/port-numbers) で確認し、 未割り当てのポート番号を選択してください。 詳細については、「 [Windows Vista および Windows Server 2008 では TCP/IP の既定の動的ポート範囲が変更されている](https://support.microsoft.com/kb/929851)」を参照してください。  
  
> [!WARNING]  
>  データベース エンジンは、再起動時に新しいポート上でリッスンを開始します。 ただし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは、レジストリを監視し、データベース エンジンが使用していない可能性があっても、構成が変更されるとすぐに新しいポート番号をレポートします。 一貫性を確保し、接続エラーを避けるために、データベース エンジンを再開します。  
  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a>SQL Server データベース エンジンに TCP/IP ポート番号を割り当てるには  
  
1.  SQL Server 構成マネージャーのコンソール ペインで、 **[SQL Server ネットワークの構成]** 、 **[\<instance name> のプロトコル]** の順に展開し、 **[TCP/IP]** をダブルクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開く際に問題がある場合は、「 [SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)」を参照してください。  
  
2.  **[TCP/IP のプロパティ]** ダイアログ ボックスの **[IP アドレス]** タブに、 **IP1**、 **IP2**という形式で **IPAll**まで IP アドレスが表示されます。 このうちいずれかが、ループバック アダプターの IP アドレス 127.0.0.1 です。 追加の IP アドレスがコンピューターの各 IP アドレスとして表示されます。 (おそらく IP バージョン 4 と IP バージョン 6 の両方のアドレスが表示されます)。各アドレスを右クリックし、 **[プロパティ]** をクリックして、構成する IP アドレスを識別します。  
  
3.  **[TCP 動的ポート]** ダイアログ ボックスには、 **が動的ポートで受信待ちすることを示す**0 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が表示されています。この 0 を削除します。  
  
     ![TCP ポート](../../database-engine/configure-windows/media/tcp-ports.png "TCP ポート")  
  
4.  [**IP**_n_ **のプロパティ**] ボックスの **[TCP ポート]** ボックスに、この IP アドレスが受信待ちするポート番号を入力し、 **[OK]** をクリックします。 複数のポートを指定する場合は、コンマで区切ります。

    > [!NOTE] 
    > **[プロトコル]** タブの **[すべて受信待ち]** 設定が [はい] に設定されている場合、 **[IPAll]** セクションの **[TCP ポート]** と **[TCP 動的ポート]** の値のみが使用され、個々の **[IP**_n]_ セクションは完全に無視されます。 **[すべて受信待ち]** の設定が [いいえ] に設定されている場合、 **[IPAll]** セクションの **[TCP ポート]** と **[TCP 動的ポート]** の設定は無視され、個々の **[IP**_n]_ セクションの **[TCP ポート]** 、 **[TCP 動的ポート]** 、および **[有効]** の設定が代わりに使用されます。
    > 各 **[IP**_n]_ セクションには、既定値が [いいえ] の **[有効]** 設定があります。[いいえ] では、ポートが定義されている場合でも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でこの IP アドレスは無視されます。  
  
5.  コンソール ペインで、 **[再起動]** をクリックします。  
  
6.  詳細ペインで、 **[SQL Server (** \<instance name> **)]** を右クリックします。 **[再起動]** をクリックして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止し、再起動します。  
  
## <a name="connecting"></a>接続  
特定のポートで受信待ちするように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を構成した後、次の 3 つの方法でクライアント アプリケーションを使用して特定のポートに接続できます。  
  
-   サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行し、名前を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続する。  
-   ポート番号を指定してクライアント上に別名を作成する。  
-   クライアントで、カスタム接続文字列を使用して接続するように指定します。  
  
## <a name="see-also"></a>参照  
 [クライアントが使用するサーバーの別名の作成または削除 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [SQL Server Browser サービス](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
