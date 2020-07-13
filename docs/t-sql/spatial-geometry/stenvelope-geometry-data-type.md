---
title: STEnvelope (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEnvelope_TSQL
- STEnvelope (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STEnvelope (geometry Data Type)
ms.assetid: 781d22e9-38df-4c23-836f-6dd0bdef49c5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4c2d8650f5a0ab1f8fe30569f9f5a096cf006605
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762520"
---
# <a name="stenvelope-geometry-data-type"></a>STEnvelope (geometry データ型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

最小軸に沿って外接する、インスタンスの四角形を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
STEnvelope ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
## <a name="examples"></a>例  
 `STGeomFromText()` を使用して `LineString` インスタンスをテキストから (0,0) ～ (2,3) の範囲で作成し、`STEnvelope()` を使用して `LineString` に外接する四角形を返す例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STEnvelope().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

