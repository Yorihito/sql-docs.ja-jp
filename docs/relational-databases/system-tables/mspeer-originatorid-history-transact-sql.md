---
description: MSpeer_originatorid_history (Transact-SQL)
title: MSpeer_originatorid_history (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 957ec6b764e18043aab4d68acff4db056cefb2fd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469038"
---
# <a name="mspeer_originatorid_history-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  トポロジに定義された発信元 ID ごとに 1 行のデータを格納します。 これには、アクティブではなくなったノードの ID が含まれています。 このテーブルは、競合検出の対象とする新しいノードを構成する際、指定した発信元 ID が既に使用されていないかどうかを確認するために使用されます。 このテーブルは、パブリケーションデータベースに格納されます。 競合検出の詳細については、「 [ピアツーピアレプリケーションでの競合の検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|発信者 ID が指定されたパブリケーションです。|  
|originator_id|**int**|競合検出のためにトポロジ内の各ノードを識別する番号|  
|originator_node|**sysname**|発信元 ID が指定されたサーバーインスタンス。|  
|originator_db|**sysname**|発信元 ID が指定されたパブリケーションデータベース。|  
|originator_db_version|**int**|発信元のデータベースのバージョン番号識別子。|  
|originator_version|**int**|パブリッシャーのバージョン番号を識別します。|  
|inserted_date|**datetime**|発信元 ID の行がこのテーブルに挿入された日付と時刻。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
