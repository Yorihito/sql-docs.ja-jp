---
title: TABLE_PRIVILEGES (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLE_PRIVILEGES_TSQL
- TABLE_PRIVILEGES
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.TABLE_PRIVILEGES view
- TABLE_PRIVILEGES view
ms.assetid: 70269d26-b085-4a98-8a9f-b4742c2848bd
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 86bd404320063ec134f18c1707ff8c12470e42a2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783058"
---
# <a name="table_privileges-transact-sql"></a>TABLE_PRIVILEGES (Transact-sql)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  現在のデータベースの現在のユーザーによって許可または付与されているテーブル権限ごとに1行のデータを返します。  
  
 これらのビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定し**ます。**_view_name_。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**GRANTOR**|**nvarchar (** 128 **)**|特権の権限の与え。|  
|**GRANTEE**|**nvarchar (** 128 **)**|権限の付与対象ユーザー。|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|テーブル修飾子。|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|テーブルを含むスキーマの名前。<br /><br /> <strong> \* \* 重要 \* : \* </strong>オブジェクトのスキーマを検索する信頼できる方法は、sys. objects カタログビューに対してクエリを実行することだけです。|  
|**TABLE_NAME**|**sysname**|テーブル名。|  
|**PRIVILEGE_TYPE**|**varchar (** 10 **)**|特権の種類。|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|権限付与対象ユーザーが他のユーザーに権限を許可できるかどうかを指定します。|  
  
## <a name="see-also"></a>関連項目  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [database_permissions &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)  
  
  
