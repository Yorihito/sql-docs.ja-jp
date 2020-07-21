---
title: min memory per query サーバー構成オプションの構成 | Microsoft Docs
description: min memory per query オプションを使用して、最小のメモリ許可を指定する方法や、SQL Server によってクエリに割り当てられる最小キロバイト数を指定する方法について説明します。
ms.custom: ''
ms.date: 11/24/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
- min memory grant
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 784dc57403cdb5c8dad6ba3e8f910ecd6d4dee26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85696850"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>min memory per query サーバー構成オプションの構成
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このトピックでは、 **または** を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] min memory per query [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。 **min memory per query** オプションは、クエリの実行用に割り当てる最小メモリ容量 (KB 単位) を指定します。 これは、最小メモリ許可とも呼ばれます。 たとえば、 **min memory per query** を 2,048 KB に設定すると、クエリには少なくともその値分のメモリが必ず割り当てられます。 既定値は 1,024 KB です。 最小値は 512 KB、最大値は 2,147,483,647 KB (2 GB) です。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Recommendations (推奨事項)](#Recommendations)  
  
     [Security](#Security)  
  
-   **以下を使用して min memory per query オプションを構成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:** [min memory per query オプションを構成した後](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   min memory per query オプションの値は、[index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) オプションよりも優先順位が高くなります。 両方のオプションを変更し、index create memory の設定値を min memory per query より小さくした場合は、警告メッセージが表示されます。ただし、値はそのまま設定されます。 クエリ実行中にも同様の警告が表示されます。  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> 推奨事項  
  
-   このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロフェッショナルだけが変更するようにしてください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ プロセッサは、クエリに割り当てる最適なメモリの量を決定しようとします。 min memory per query オプションを使用すると、管理者は、どの単一のクエリにも割り当てられるメモリ量の最小値を指定できます。 通常、クエリが大量のデータに対してハッシュおよび並べ替え操作を行う場合は、min memory per query オプションの設定よりも多くメモリがクエリに割り当てられます。 min memory per query の値を増やすと、小規模から中規模のクエリではパフォーマンスが向上する可能性があります。ただし、この値の増加によって、メモリ リソースでの競合も増加する可能性があります。 min memory per query オプションには、並べ替え操作用に割り当てられるメモリが含まれます。  

-    min memory per query サーバー構成オプションは、特に稼働率が高いシステムではあまり大きい値を設定しないでください。これは、要求されたメモリ最小量を確保するか、query wait サーバー構成オプションに指定された値を超えるまで、クエリは待機する必要があるためです<sup>1</sup>。 クエリの実行に最小限必要として指定されている量よりも多くのメモリが実際に使用できる場合、そのクエリがメモリを有効に利用できるという条件の基に、クエリで追加のメモリが利用可能になります。     

<sup>1</sup> このシナリオの場合、待機の種類は一般的に RESOURCE_SEMAPHORE になります。 詳細については、「[sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)」を参照してください。

###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>min memory per query オプションを構成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[メモリ]** ノードをクリックします。  
  
3.  **[クエリごとに使用する最小メモリ (KB 単位)]** ボックスで、クエリの実行用に割り当てる最小メモリ容量 (KB 単位) を指定します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>min memory per query オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して、 `min memory per query` オプションの値を `3500` KB に設定する方法を示します。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO    
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a>補足情報: min memory per query オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [index create memory サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md)     
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)     
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)
  
  
