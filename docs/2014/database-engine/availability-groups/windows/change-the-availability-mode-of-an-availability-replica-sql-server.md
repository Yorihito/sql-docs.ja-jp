---
title: 可用性レプリカの可用性モードの変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1636f3ea86e083e47276423b120dbc8d3744d387
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937063"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a>可用性レプリカの可用性モードの変更 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]の AlwaysOn 可用性グループでの可用性レプリカの可用性モードを変更する方法について説明します。 可用性モードは、レプリカによるコミットが非同期か同期かを制御するレプリカ プロパティです。 *非同期コミット モード* は、高可用性を犠牲にしてパフォーマンスを最大限に高めるものであり、 *強制フェールオーバー*と通常呼ばれる強制手動フェールオーバー (データ損失の可能性あり) のみをサポートしています。 *同期コミット モード* は、パフォーマンスよりも高可用性を重視し、セカンダリ レプリカの同期後は手動でのフェールオーバーをサポートします (必要に応じて、自動フェールオーバーもサポートします)。  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> 前提条件  
  
-   プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **可用性グループの可用性モードを変更するには**  
  
1.  オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。  
  
2.  **[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。  
  
3.  変更するレプリカが含まれる可用性グループをクリックします。  
  
4.  レプリカを右クリックし、 **[プロパティ]** をクリックします。  
  
5.  **[可用性レプリカ プロパティ]** ダイアログ ボックスで **[可用性モード]** ボックスの一覧を使用して、このレプリカの可用性モードを変更します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 **可用性グループの可用性モードを変更するには**  
  
1.  プライマリ レプリカをホストするサーバー インスタンスに接続します。  
  
2.  [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。  
  
     ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     } )  
  
     *group_name* の部分には、可用性グループの名前を指定します。 *server_name* の部分には、変更するレプリカがホストされているサーバー インスタンスの名前を指定します。  
  
    > [!NOTE]  
    >  FAILOVER_MODE = AUTOMATIC は、AVAILABILITY_MODE = SYNCHRONOUS_COMMIT も指定した場合にのみサポートされます。  
  
     次の例は、 `AccountsAG` 可用性グループのプライマリ レプリカに入力すると、 `INSTANCE09` サーバー インスタンスでホストされるレプリカの可用性モードを同期コミット、フェールオーバー モードを自動フェールオーバーに変更します。  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell の使用

### <a name="to-change-the-availability-mode-of-an-availability-group"></a>可用性グループの可用性モードを変更するには
  
1.  プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。  
  
2.  `Set-SqlAvailabilityReplica` コマンドレットを `AvailabilityMode` パラメーターと共に使用し、必要に応じて `FailoverMode` パラメーターを指定します。  
  
     たとえば、次のコマンドは、可用性グループ `MyReplica` のレプリカ `MyAg` を、同期コミット可用性モードを使用し、自動フェールオーバーをサポートするように変更します。  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)   
 [フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md)  
