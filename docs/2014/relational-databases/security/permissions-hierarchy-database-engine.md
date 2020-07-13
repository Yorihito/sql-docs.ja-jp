---
title: 権限の階層 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9a04e5595e509de63b362b31b240e113e635581d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063173"
---
# <a name="permissions-hierarchy-database-engine"></a>権限の階層 (データベース エンジン)
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] では、権限を使用してセキュリティで保護できるエンティティの階層コレクションが管理されています。 これらのエンティティを、 *セキュリティ保護可能なリソース*と呼びます。 最も顕著なセキュリティ保護可能なリソースはサーバーとデータベースですが、さらに細かいレベルで個別の権限を設定できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 適切な権限が許可されていることを確認することにより、セキュリティ保護可能なリソースに対するプリンシパルによる操作を制御しています。

 次の図は、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の権限階層における関係を示します。

 ![データベース エンジンの権限の階層の図](../../database-engine/media/wj-security-layers.gif "データベース エンジンの権限の階層の図")

## <a name="chart-of-sql-server-permissions"></a>SQL Server 権限の一覧表
 Pdf 形式のすべてのアクセス許可のポスターサイズのグラフについ [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ては、「」を参照してください [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf) 。

## <a name="working-with-permissions"></a>権限を使用した作業
 権限は、使い慣れた [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ (RANT、DENY、REVOKE) で操作できます。 権限に関する情報は、 [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) カタログ ビューおよび [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) カタログ ビューに表示されます。 組み込み関数を使用して権限に関する情報をクエリすることもできます。

## <a name="see-also"></a>参照
 SQL Server の[データベースエンジン &#40;権限](permissions-database-engine.md)の[セキュリティ保護](securing-sql-server.md)&#41;[Securables](securables.md) [プリンシパル &#40;](authentication-access/principals-database-engine.md)データベースエンジン&#41;[GRANT &#40;](/sql/t-sql/statements/grant-transact-sql) transact-sql&#41;[REVOKE](/sql/t-sql/statements/revoke-transact-sql) &#40;&#41;&#40;[&#41;transact-sql HAS_PERMS_BY_NAME](/sql/t-sql/statements/deny-transact-sql) &#40;[&#41;transact-sql fn_builtin_permissions](/sql/t-sql/functions/has-perms-by-name-transact-sql) &#40;&#41;transact-sql server_permissions &#40;&#41;[transact-sql database_permissions &#40;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)を&#41;を[sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) transact-sql を[し](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)ます。


