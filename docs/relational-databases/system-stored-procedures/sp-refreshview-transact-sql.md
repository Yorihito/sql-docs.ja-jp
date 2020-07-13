---
title: sp_refreshview (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refreshview
- sp_refreshview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refreshview
ms.assetid: 9ce1d07c-ee66-4a83-8c73-cd2cc104dd08
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dbc12b5e9013e8cbb5fb223f473e68c2e1cab445
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891508"
---
# <a name="sp_refreshview-transact-sql"></a>sp_refreshview (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  指定された非スキーマ バインド ビューのメタデータを更新します。 ビューが依存している基になるオブジェクトが変更されたため、ビューの永続的なメタデータが古くなることがあります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_refreshview [ @viewname = ] 'viewname'   
```  
  
## <a name="arguments"></a>引数  
`[ @viewname = ] 'viewname'`ビューの名前を指定します。 *viewname*は**nvarchar**,、既定値はありません。 *viewname*にはマルチパート識別子を指定できますが、参照できるのは現在のデータベース内のビューのみです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または0以外の数値 (失敗)  
  
## <a name="remarks"></a>注釈  
 ビューが schemabinding で作成されていない場合は、ビューの定義に影響を与えるビューの基になるオブジェクトに対して変更が行われたときに**sp_refreshview**を実行する必要があります。 それ以外の場合は、ビューのクエリ時に、予期しない結果が生成される可能性があります。  
  
## <a name="permissions"></a>アクセス許可  
 ビューに対する ALTER 権限と、共通言語ランタイム (CLR) ユーザー定義型およびビュー列で参照される XML スキーマ コレクションに対する REFERENCES 権限が必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-updating-the-metadata-of-a-view"></a>A. ビューのメタデータの更新  
 次の例では、ビュー `Sales.vIndividualCustomer` のメタデータを更新します。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sp_refreshview N'Sales.vIndividualCustomer';  
```  
  
### <a name="b-creating-a-script-that-updates-all-views-that-have-dependencies-on-a-changed-object"></a>B: 変更されたオブジェクトに依存関係があるすべてのビューを更新するスクリプトを作成する  
 テーブル `Person.Person` に対して作成された任意のビューの定義に影響を与える形で、このテーブルが変更されたとします。 次の例では、テーブル `Person.Person` に対する依存関係があるすべてのビューについて、メタデータを更新するスクリプトを作成しています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT 'EXEC sp_refreshview ''' + name + ''''   
FROM sys.objects AS so   
INNER JOIN sys.sql_expression_dependencies AS sed   
    ON so.object_id = sed.referencing_id   
WHERE so.type = 'V' AND sed.referenced_id = OBJECT_ID('Person.Person');  
```  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_refreshsqlmodule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md)  
  
  
