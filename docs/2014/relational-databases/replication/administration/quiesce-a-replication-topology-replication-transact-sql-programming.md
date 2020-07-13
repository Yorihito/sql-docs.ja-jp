---
title: レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12f0fb8ee3a6118e03799d17836573fb5c733df
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061553"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a>レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング)
   システムの*停止*を実行するには、すべてのノードのパブリッシュされたテーブルで処理を停止し、他のすべてのノードからのすべての変更を各ノードが受信しているかどうかを確認します。 このトピックでは、いくつかの管理タスクで必要とされる、レプリケーション トポロジの停止方法や、他のノードからのすべての変更をノードが受け取ったことを確認する方法について説明します。  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a>読み取り専用サブスクライバーを含むトランザクション レプリケーション トポロジを停止するには  
  
1.  パブリッシャーで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  パブリッシャー側のパブリケーション データベースに対して、[sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql) を実行します。  
  
3.  パブリッシャー側のパブリケーション データベースに対して、 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)を実行します。  
  
4.  各サブスクライバーがトレーサー トークンを受け取ったことを確認します。  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a>更新可能サブスクリプションを含むトランザクション レプリケーション トポロジを停止するには  
  
1.  パブリッシャーおよびすべてのサブスクライバーで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  キュー更新サブスクリプションを使用するサブスクライバーがある場合  
  
    1.  キュー リーダー エージェントが連続モードで実行されていない場合は、エージェントを実行します。 エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。  
  
    2.  キューが空であることを確認するには、各サブスクライバーで [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) を実行します。  
  
3.  パブリッシャー側のパブリケーション データベースに対して、 [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)を実行します。  
  
4.  パブリッシャー側のパブリケーション データベースに対して、 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)を実行します。  
  
5.  各サブスクライバーがトレーサー トークンを受け取ったことを確認します。  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a>ピア ツー ピアのトランザクション レプリケーション トポロジを停止するには  
  
1.  すべてのノードで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  トポロジ内の各パブリケーション データベースで [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) を実行します。  
  
3.  ログ リーダー エージェントまたはディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。 ログ リーダー エージェントは、ディストリビューション エージェントの前に開始する必要があります。 エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。  
  
4.  トポロジ内の各パブリケーション データベースで [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) を実行します。 結果セットに他のノードからの応答が含まれていることを確認します。  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a>ピア ツー ピア ノードが前の変更をすべて受け取ったことを確認するには  
  
1.  チェックする対象のノードのパブリケーション データベースで [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) を実行します。  
  
2.  ログ リーダー エージェントまたはディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。 ログ リーダー エージェントは、ディストリビューション エージェントの前に開始する必要があります。 エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。  
  
3.  チェックする対象のノードのパブリケーション データベースで [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) を実行します。 結果セットに他のノードからの応答が含まれていることを確認します。  
  
### <a name="to-quiesce-a-merge-replication-topology"></a>マージ レプリケーション トポロジを停止するには  
  
1.  パブリッシャーおよびすべてのサブスクライバーで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  各サブスクリプションに対して、マージ エージェントを 2 回実行します。すべてのサブスクリプションを 1 回同期させてから、各サブスクリプションをもう 1 回同期させます。 これにより、すべての変更がすべてのノードに確実にレプリケートされます。 エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。  
  
    > [!NOTE]  
    >  同期中に競合が発生した場合は、マージ エージェントを 2 回実行した後でも、競合の解決に必要な変更が全ノードに反映されない可能性があります。  
  
## <a name="see-also"></a>参照  
 [ピアツーピアトポロジの管理 &#40;レプリケーション Transact-sql プログラミング&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
