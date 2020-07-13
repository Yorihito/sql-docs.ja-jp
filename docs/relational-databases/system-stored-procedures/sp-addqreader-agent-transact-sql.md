---
title: sp_addqreader_agent (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqreader_agent_TSQL
- sp_addqreader_agent
helpviewer_keywords:
- sp_addqreader_agent
ms.assetid: dc9f591a-e67e-4ba8-bf47-defd5eda0822
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1758f6cd269c911ea582577721d29e6534910e91
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716456"
---
# <a name="sp_addqreader_agent-transact-sql"></a>sp_addqreader_agent (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  指定されたディストリビューターのキューリーダーエージェントを追加します。 このストアドプロシージャは、ディストリビューター側のディストリビューションデータベース、またはパブリッシャー側のパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addqreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name'  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>引数  
`[ @job_login = ] 'job_login'`[!INCLUDE[msCoName](../../includes/msconame-md.md)]エージェントを実行する Windows アカウントのログインを指定します。 *job_login*は**nvarchar (257)**,、既定値はありません。 この Windows アカウントは、ディストリビューターへのエージェント接続に常に使用されます。  
  
`[ @job_password = ] 'job_password'`エージェントを実行する Windows アカウントのパスワードを指定します。 *job_password*は**sysname**であり、既定値はありません。  
  
> [!IMPORTANT]  
>  認証情報をスクリプトファイルに保存しないでください。 セキュリティを最大限に高めるには、ログイン名とパスワードを実行時に指定する必要があります。  
  
`[ @job_name = ] 'job_name'`既存のエージェントジョブの名前を指定します。 *job_name*は**sysname**で、既定値は NULL です。 このパラメーターは、新しく作成されたジョブ (既定値) ではなく、既存のジョブを使用してエージェントが作成された場合にのみ指定します。  
  
`[ @frompublisher = ] frompublisher`プロシージャがパブリッシャーで実行されているかどうかを指定します。 *frompublisher*の部分は bit で、既定値は**0**です。 値**1**は、パブリケーションデータベースのパブリッシャーからプロシージャが実行されていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addqreader_agent**は、トランザクションレプリケーションで使用します。  
  
 **sp_addqreader_agent**は、 [sp_adddistributiondb](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)後のキュー更新をサポートするディストリビューターで少なくと[sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)も1回実行する必要があります。  
  
 [Sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)を実行すると、キューリーダーエージェントジョブは削除されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_addqreader_agent**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [トランザクションパブリケーションの更新サブスクリプションを有効にする](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [レプリケーションスクリプトのアップグレード &#40;レプリケーション Transact-sql プログラミング&#41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [トランザクションレプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_changeqreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md)   
 [sp_helpqreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)  
  
  
