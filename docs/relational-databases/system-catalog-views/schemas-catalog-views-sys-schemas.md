---
title: sys. スキーマ (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2f4aa79f2c93e1c78c895f0e3d47e3114df20a8c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834457"
---
# <a name="schemas-catalog-views---sysschemas"></a>スキーマカタログビュー-sys スキーマ
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  データベーススキーマごとに1行のデータを格納します。  
  
> [!NOTE]  
>  データベース スキーマは、XML ドキュメントのコンテンツ モデルの定義に使用される XML スキーマとは異なります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|スキーマの名前。 データベース内で一意です。|  
|**schema_id**|**int**|スキーマの ID です。 データベース内で一意です。|  
|**principal_id**|**int**|このスキーマを所有するプリンシパルの ID。|  
  
## <a name="remarks"></a>解説  
データベーススキーマは、テーブル、ビュー、プロシージャ、関数など、オブジェクトの名前空間またはコンテナーとして機能します。これは、**のカタログビュー**にあります。  

各スキーマには所有者があります。 所有者はセキュリティ[プリンシパル](../../relational-databases/security/authentication-access/principals-database-engine.md)です。
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[プリンシパル](../../relational-databases/security/authentication-access/principals-database-engine.md)

[カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   

[スキーマカタログビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   

[sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
