---
title: sp_add_category (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_category
- sp_add_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_category
ms.assetid: 6cca32cd-d941-4378-aed6-a7c90cb7520a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 251c9992285084123df7afb3c27678c2886b531c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880004"
---
# <a name="sp_add_category-transact-sql"></a>sp_add_category (Transact-sql)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  指定されたジョブ、警告、またはオペレーターのカテゴリをサーバーに追加します。 別の方法については、「 [SQL Server Management Studio を使用したジョブカテゴリの作成](/sql/ssms/agent/create-a-job-category)」を参照してください。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 > [!IMPORTANT]  
 > [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_category   
     [ [ @class = ] 'class', ]   
     [ [ @type = ] 'type', ]   
     { [ @name = ] 'name' }  
```  
  
## <a name="arguments"></a>引数  
`[ @class = ] 'class'`追加するカテゴリのクラス。 *クラス*は**varchar (8)** で、既定値は JOB,、これらの値のいずれかを指定することができます。  
  
|[値]|説明|  
|-----------|-----------------|  
|ジョブ|ジョブカテゴリを追加します。|  
|ALERT|アラートカテゴリを追加します。|  
|OPERATOR|オペレーターカテゴリを追加します。|  
  
`[ @type = ] 'type'`追加するカテゴリの種類。 *型*は**varchar (12)**,、既定値は**LOCAL**,、これらの値のいずれかを指定することができます。  
  
|[値]|説明|  
|-----------|-----------------|  
|LOCAL|ローカル ジョブ カテゴリ|  
|マルチサーバー|マルチサーバージョブカテゴリ。|  
|なし|JOB 以外のクラスのカテゴリ **。**|  
  
`[ @name = ] 'name'`追加するカテゴリの名前。 名前は、指定されたクラス内で一意である必要があります。 *名前*は**sysname**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_add_category**は、 **msdb**データベースから実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_add_category**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="examples"></a>使用例  
 次の例では、`AdminJobs` というローカル ジョブ カテゴリを作成します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_category  
    @class=N'JOB',  
    @type=N'LOCAL',  
    @name=N'AdminJobs' ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sp_delete_category &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Transact-sql&#41;&#40;ジョブのdbo.sys](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)   
 [dbo.sysjobservers &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
