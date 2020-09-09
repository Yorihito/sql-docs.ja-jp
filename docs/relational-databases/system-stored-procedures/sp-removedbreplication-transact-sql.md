---
title: sp_removedbreplication (T-sql)
description: SQL Server レプリケーション用にパブリケーションデータベースのすべてのレプリケーションオブジェクトを削除するために使用する sp_removedbreplication ストアドプロシージャについて説明します。
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_removedbreplication
- sp_removedbreplication_TSQL
helpviewer_keywords:
- sp_removedbreplication
ms.assetid: cb98d571-d1eb-467b-91f7-a6e091009672
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 01fc666444891836011b80e77492b1cdebbefff5
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538656"
---
# <a name="sp_removedbreplication-transact-sql"></a>sp_removedbreplication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  このストアド プロシージャにより、SQL Server のパブリッシャー インスタンス側のパブリケーション データベース、または SQL Server のサブスクライバー インスタンス側のサブスクリプション データベースから、すべてのレプリケーション オブジェクトが削除されます。 適切なデータベースで実行するか、または同じインスタンスにある別のデータベースのコンテキストで実行する場合は、レプリケーション オブジェクトを削除するデータベースを指定します。 このプロシージャでは、ディストリビューション データベースなどその他のデータベースからオブジェクトが削除されることはありません。  
  
> [!NOTE]  
>   このプロシージャは、他の方法でレプリケーション オブジェクトを削除できなかった場合にのみ使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_removedbreplication [ [ @dbname = ] 'dbname' ]  
    [ , [ @type = ] type ]   
```  
  
## <a name="arguments"></a>引数  
`[ @dbname = ] 'dbname'` データベースの名前を指定します。 *dbname* のデータ型は **sysname**で、既定値は NULL です。 NULL の場合は、現在のデータベースが使用されます。  
  
`[ @type = ] type` データベースオブジェクトを削除するレプリケーションの種類を指定します。 *種類* は **nvarchar (5)** で、次のいずれかの値を指定できます。  
  
|||  
|-|-|  
|**さん**|トランザクション レプリケーション パブリッシング オブジェクトを削除。|  
|**merge**|マージ レプリケーション パブリッシング オブジェクトを削除。|  
|**both** (既定値)|すべてのレプリケーション パブリッシング オブジェクトを削除。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_removedbreplication** は、すべての種類のレプリケーションで使用されます。  
  
 **sp_removedbreplication** は、復元する必要のあるレプリケーションオブジェクトを持たないレプリケートされたデータベースを復元する場合に便利です。  
  
 **sp_removedbreplication** は、読み取り専用としてマークされているデータベースに対しては使用できません。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/sp-removedbreplication-t_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_removedbreplication**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="example"></a>例  
  
```  
-- Remove replication objects from the subscription database on MYSUB.  
DECLARE @subscriptionDB AS sysname  
SET @subscriptionDB = N'AdventureWorksReplica'  
  
-- Remove replication objects from a subscription database (if necessary).  
USE master  
EXEC sp_removedbreplication @subscriptionDB  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
