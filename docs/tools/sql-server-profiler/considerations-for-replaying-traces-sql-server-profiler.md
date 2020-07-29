---
title: トレースの再生に関する注意点
titleSuffix: SQL Server Profiler
description: SQL Server Profiler でトレースを再生できない原因となっている操作、ストアド プロシージャ、テンプレート、およびログ アクティビティについて説明します。
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.openlocfilehash: 1a54aaca0506b1b9d25a900ea2787b9427b14209
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774902"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>トレースの再生に関する注意点 (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、次の種類のトレースを再生できません。  
  
-   トランザクション レプリケーションや他のトランザクションのログ利用状況を含むトレース。 このようなイベントはスキップされます。 他の種類のレプリケーションではトランザクション ログが記録されないので、そのようなレプリケーションは影響を受けません。  
  
-   グローバル一意識別子 (GUID) を必要とする操作を含むトレース。 このようなイベントはスキップされます。  
  
-   **bcp**ユーティリティ、BULK INSERT、READTEXT、WRITETEXT、UPDATETEXT ステートメントを必要とする **text**列、 **ntext** 列、および **image** 列での操作やフルテキスト操作を含むトレース。 このようなイベントはスキップされます。  
  
-   セッションをバインドする **sp_getbindtoken** および **sp_bindsession** システム ストアド プロシージャを含むトレース。 このようなイベントはスキップされます。  
  
> [!NOTE]  
>  あらかじめ構成された再生テンプレート (**TSQL_Replay**) を使用せず、必要なすべてのデータをキャプチャしていないトレースは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では再生されません。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
 トレースの再生に必要な権限の詳細については、「 [SQL Server Profiler の実行に必要な権限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [SQL Server イベント クラスの参照](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [sp_bindsession &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [READTEXT &#40;Transact-SQL&#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
