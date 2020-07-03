---
title: sysextendedarticlesview (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysextendedarticlesview_TSQL
- sysextendedarticlesview
dev_langs:
- TSQL
helpviewer_keywords:
- sysextendedarticlesview view
ms.assetid: 8bdd22f7-c268-49b6-820c-3fe603feb128
author: stevestein
ms.author: sstein
ms.openlocfilehash: c273b33c0bdecd86eb9ef21f086860bbe3c569b5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881261"
---
# <a name="sysextendedarticlesview-transact-sql"></a>sysextendedarticlesview (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **Sysextendedarticlesview**ビューには、パブリッシュされたアーティクルに関する情報が表示されます。 このビューは、ディストリビューション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID 番号を示す ID 列です。|  
|**creation_script**|**nvarchar(255)**|アーティクルのスキーマ作成スクリプトです。|  
|**del_cmd**|**nvarchar(255)**|DELETE 時に実行するコマンドです。それ以外の場合は、ログから構築します。|  
|**description**|**nvarchar(255)**|アーティクルの説明エントリです。|  
|**dest_table**|**nvarchar(128)**|対象テーブルの名前です。|  
|**filter**|**int**|行方向のパーティション分割に使用されるストアドプロシージャのオブジェクト識別子。|  
|**filter_clause**|**ntext**|行方向のフィルター選択に使用される、アーティクルの WHERE 句。|  
|**ins_cmd**|**nvarchar(255)**|挿入時に実行するコマンドです。|  
|**name**|**nvarchar(128)**|アーティクルに関連付けられた名前です。パブリケーション内で一意です。|  
|**objid**|**int**|パブリッシュされたテーブルオブジェクト ID です。|  
|**pubid**|**int**|アーティクルが属しているパブリケーションの ID。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE、または TRUNCATE の事前作成コマンド。<br /><br /> **0** = なし。<br /><br /> **1** = DROP。<br /><br /> **2** = 削除します。<br /><br /> **3** = 切り捨て。|  
|**status**|**int**|アーティクルのオプションと状態のビットマスク。これらの値の1つ以上のビットごとの論理和演算を実行できます。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含めます。<br /><br /> **16** = パラメーター化されたステートメントを使用します。<br /><br /> **24** = INSERT ステートメントに列名を含め、パラメーター化されたステートメントを使用します。<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクルの場合、この列の値は17になります。 値0は、アーティクルが非アクティブであり、追加のプロパティが定義されていないことを示します。|  
|**sync_objid**|**int**|アーティクルの定義を表すテーブルまたはビューの ID です。|  
|**type**|**tinyint**|アーティクルのタイプです。<br /><br /> **1** = ログベースのアーティクル。<br /><br /> **3** = 手動フィルターを使用したログベースのアーティクル。<br /><br /> **5** = 手動ビューを使用したログベースのアーティクル。<br /><br /> **7** = 手動フィルターと手動ビューを使用するログベースのアーティクル。|  
|**upd_cmd**|**nvarchar(255)**|更新時に実行するコマンドです。それ以外の場合は、ログから構築します。|  
|**schema_option**|**[バイナリ]**|パブリッシュされたオブジェクトのどのプロパティをスナップショットにスクリプト作成するのかを示します。 サポートされているスキーマオプションの一覧については、「 [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)」を参照してください。|  
|**dest_owner**|**nvarchar(128)**|転送先データベースのテーブルの所有者を指定します。|  
|**ins_scripting_proc**|**int**|INSERT ステートメントがレプリケートされるときに実行されるカスタムストアドプロシージャまたはスクリプトのオブジェクト識別子。|  
|**del_scripting_proc**|**int**|DELETE ステートメントがレプリケートされるときに実行されるカスタム ストアド プロシージャまたはスクリプトのオブジェクト識別子です。|  
|**upd_scripting_proc**|**int**|UPDATE ステートメントがレプリケートされるときに実行されるカスタムストアドプロシージャまたはスクリプトのオブジェクト識別子。|  
|**custom_script**|**int**|DDL トリガーの完了時に実行されるカスタムスクリプトまたはプロシージャのオブジェクト識別子。|  
|**fire_triggers_on_snapshot**|**int**|スナップショットが適用されるときにレプリケートされたトリガーが実行されるかどうかを示します。次のいずれかの値をとります。<br /><br /> **0** = トリガーは実行されません。<br /><br /> **1** = トリガーが実行されます。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;Transact-sql&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
