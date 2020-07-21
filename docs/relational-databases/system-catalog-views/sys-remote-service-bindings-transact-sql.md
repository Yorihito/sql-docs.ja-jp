---
title: remote_service_bindings (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 76ef28d83fca3fd0eb904f0d98b798866b9715eb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896478"
---
# <a name="sysremote_service_bindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このカタログビューには、リモートサービスバインドごとに1行が含まれています。 
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|このリモートサービスバインドの名前。 NULL 値は許容されません。|  
|**remote_service_binding_id**|**int**|このリモートサービスバインドの ID。 NULL 値は許容されません。|  
|**principal_id**|**int**|このリモートサービスバインドを所有するデータベースプリンシパルの ID。 NULLABLE.|  
|**remote_service_name**|**nvarchar(256)**|このバインディングが適用されるリモートサービスの名前。 NULLABLE.|  
|**service_contract_id**|**int**|このバインディングが適用されるコントラクトの ID。 値0は、このバインディングがサービスのすべてのコントラクトに適用されることを意味するワイルドカードです。 NULL 値は許容されません。|  
|**remote_principal_id**|**int**|リモートサービスバインドで指定されたユーザーの ID。 Service Broker では、このユーザーが所有する証明書を使用して、指定したコントラクトに基づき、指定したサービスと通信します。 NULLABLE.|  
|**is_anonymous_on**|**bit**|このリモートサービスバインドは、匿名セキュリティを使用します。 メッセージ交換を開始するユーザーの id が、発信先サービスに提供されていません。 NULL 値は許容されません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
