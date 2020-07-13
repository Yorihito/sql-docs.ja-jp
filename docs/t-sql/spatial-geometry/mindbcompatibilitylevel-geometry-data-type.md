---
title: MinDbCompatibilityLevel (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c4407c6a6725a1fa19382b2bc91aa7567f56e7a3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759500"
---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel (geometry データ型)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

**geometry** データ型のインスタンスを認識する最小データベース互換性レベルを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **int**  
  
 CLR の戻り値の型: **int**  
  
## <a name="remarks"></a>解説  
 `MinDbCompatibilityLevel()` を使用すると、データベースで互換性レベルを変更する前に、空間オブジェクトの互換性をテストできます。  
  
## <a name="examples"></a>例  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. 互換性レベル 110 で CircularString 型の互換性をテストする  
 次の例では、`CircularString` インスタンスの、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との互換性がテストされます。  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 110 
 BEGIN 
 SELECT @g.ToString(); 
 END
 ```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. 互換性レベル 100 で LineString 型の互換性をテストする  
 次の例では、`LineString` インスタンスの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] との互換性をテストします。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 100 
 BEGIN 
 SELECT @g.ToString(); 
 END
``` 
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE 互換性レベル &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

