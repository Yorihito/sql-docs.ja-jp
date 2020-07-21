---
title: registered_search_property_lists (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- registered_search_property_lists_TSQL
- sys.registered_search_property_lists
- registered_search_property_lists
- sys.registered_search_property_lists_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- sys.registered_search_property_lists catalog view
- search property lists [SQL Server], viewing
ms.assetid: 630d4caa-9bea-4cd3-a5b1-01098b0855fc
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 0ed0c0a3e0a7a8e25279090fb0a84ccbad9d9a2b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897751"
---
# <a name="sysregistered_search_property_lists-transact-sql"></a>sys.registered_search_property_lists (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  現在のデータベースの検索プロパティ リストごとに 1 行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**property_list_id**|**int**|プロパティ リストの ID。|  
|**name**|**sysname**|プロパティ リストの名前。|  
|**create_date**|**datetime**|プロパティ リストが作成された日付。|  
|**modify_date**|**datetime**|ALTER ステートメントによってプロパティリストが最後に変更された日付。|  
|**principal_id**|**int**|プロパティ リストの所有者。|  
  
## <a name="remarks"></a>Remarks  
 詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 検索プロパティリストでのメタデータの表示は、自分が所有しているもの、または参照権限が付与されているものに限定されます。  
  
> [!NOTE]  
>  検索プロパティリストの所有者は、一覧に対する参照または制御権限を許可できます。 CONTROL 権限を持つユーザーは、他のユーザーに REFERENCE 権限を与えることができます。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース内の検索プロパティリストの ID と名前を表示し [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] ます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT property_list_id, name FROM sys.registered_search_property_lists;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;のフルテキストインデックスの変更](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
  
