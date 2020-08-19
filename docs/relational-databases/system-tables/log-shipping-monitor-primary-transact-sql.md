---
description: log_shipping_monitor_primary (Transact-sql)
title: log_shipping_monitor_primary (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_primary
- log_shipping_monitor_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_primary system table
ms.assetid: 5f629a29-1a62-40e6-ae33-6f6b7dd09a36
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d74a594c4a8b9140f550fd02878cd4994779fe42
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446581"
---
# <a name="log_shipping_monitor_primary-transact-sql"></a>log_shipping_monitor_primary (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  各ログ配布構成内のプライマリ データベースごとに、1 つの監視レコードを格納します。 このテーブルは、 **msdb** データベースに格納されます。  
  
 履歴と監視に関連するテーブルは、プライマリサーバーとセカンダリサーバーでも使用されます。   
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**primary_id**|**uniqueidentifier**|ログ配布構成のプライマリデータベースの ID。|  
|**primary_server**|**sysname**|ログ配布構成における [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のプライマリ インスタンスの名前。|  
|**primary_database**|**sysname**|ログ配布構成のプライマリデータベースの名前。|  
|**backup_threshold**|**int**|バックアップ操作の間に、アラートが生成されるまでの経過時間 (分) です。|  
|**threshold_alert**|**int**|バックアップのしきい値を超えたときに発生するアラート。|  
|**threshold_alert_enabled**|**bit**|バックアップしきい値アラートを有効にするかどうかを決定します。 1 = 有効。<br /><br /> 0 = 無効です。|  
|**last_backup_file**|**nvarchar (500)**|最新のトランザクションログバックアップの絶対パス。|  
|**last_backup_date**|**datetime**|プライマリデータベースでの最後のトランザクションログバックアップ操作の日時。|  
|**last_backup_date_utc**|**datetime**|プライマリデータベースでの最後のトランザクションログバックアップ操作の日時。協定世界時で表されます。|  
|**history_retention_period**|**int**|指定したプライマリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>解説  
 リモート監視サーバーに格納されているだけでなく、プライマリサーバーに関連する情報は、プライマリサーバーの **log_shipping_monitor_primary** テーブルに格納されます。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)   
 [sp_change_log_shipping_primary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_help_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_help_log_shipping_monitor_primary &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql.md)   
 [sp_delete_log_shipping_alert_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql.md)   
 [システム テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
