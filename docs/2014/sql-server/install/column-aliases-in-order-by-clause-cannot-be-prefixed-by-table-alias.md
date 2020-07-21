---
title: ORDER BY 句の列の別名をテーブル別名 | で始まることはできませんMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44333d778753a2f8761d32d181681b798e3bc409
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85037086"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a>ORDER BY 句の列の別名をテーブル別名によってプレフィックス指定できない
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、ORDER BY 句の列の別名はテーブル別名によってプレフィックス指定できません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 たとえば、次のクエリは [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では実行されますが、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ではエラーが返されます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)]では `p.l` 句の `ORDER BY` がテーブル内の有効な列に一致しません。  
  
### <a name="exception"></a>例外  
 ORDER BY 句で指定された、プレフィックスの付いた列の別名が、指定したテーブルの有効な列名であれば、クエリは問題なく実行されます。[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、ステートメントのセマンティクスが異なる場合があります。 たとえば、以下のステートメントで指定された列の別名 (`id`) が `sysobjects` テーブル内の有効な列名であるとします。 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ではステートメントが実行されると、結果セットが並べ替えられた後、`CAST` 演算が実行されます。 つまり、`name` 列が並べ替え操作で使用されます。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では並べ替え操作の前に `CAST` 演算が実行されます。 つまり、テーブル内の `id` 列が並べ替え操作に使用され、結果セットが予期しない順序で返されます。  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a>修正措置  
 次の方法のいずれかを使用して、ORDER BY 句のテーブル別名によってプレフィックス指定された列の別名を使用するクエリを修正してください。  
  
-   可能な限り、ORDER BY 句の列の別名をプレフィックス指定しない。  
  
-   列の別名を列名に置き換える。  
  
 たとえば、次の両方のクエリは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では問題なく実行されます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
