---
title: 空間データ (SQL Server) | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: dccec5ca3c42f605145853b2e864e861b17535fb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063029"
---
# <a name="spatial-data-sql-server"></a>空間データ (SQL Server)
  空間データは、幾何学的オブジェクトの物理的な場所と形状に関する情報を表します。 これらのオブジェクトは、ポイントの場所や、国、道路、湖などのより複雑なオブジェクトである可能性があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`geometry` と `geography` の 2 つの空間データ型がサポートされています。  
  
-   `geometry` 型は、ユークリッド (平面) 座標系のデータを表します。  
  
-   `geography` 型は、球体地球座標系のデータを表します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、どちらのデータ型も .NET 共通言語ランタイム (CLR) のデータ型として実装されています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入された空間機能の詳細な説明とサンプルについては、ホワイト ペーパー「 [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407)」 (SQL Server 2012 の新しい空間機能) をダウンロードして参照してください。  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> 関連タスク  
 [geometry インスタンスの作成、構築、およびクエリ](create-construct-and-query-geometry-instances.md)  
 geometry データ型のインスタンスで使用できるメソッドについて説明します。  
  
 [geography インスタンスの作成、構築、およびクエリ](create-construct-and-query-geography-instances.md)  
 geography データ型のインスタンスで使用できるメソッドについて説明します。  
  
 [空間データに対するニアレスト ネイバーのクエリ](query-spatial-data-for-nearest-neighbor.md)  
 特定の空間オブジェクトに最も近い空間オブジェクトを検索するための一般的なクエリ パターンについて説明します。  
  
 [空間インデックスの作成、変更、および削除](create-modify-and-drop-spatial-indexes.md)  
 空間インデックスの作成、変更、および削除に関する情報を提供します。  
  
## <a name="related-content"></a>関連コンテンツ  
 [空間データ型の概要](spatial-data-types-overview.md)  
 空間データ型について説明します。  
  
-   [Point](point.md)  
  
-   [LineString](linestring.md)  
  
-   [CircularString](circularstring.md)  
  
-   [CompoundCurve](compoundcurve.md)  
  
-   [Polygon](polygon.md)  
  
-   [CurvePolygon](curvepolygon.md)  
  
-   [MultiPoint](multipoint.md)  
  
-   [MultiLineString](multilinestring.md)  
  
-   [MultiPolygon](multipolygon.md)  
  
-   [GeometryCollection](geometrycollection.md)  
  
 [空間インデックスの概要](spatial-indexes-overview.md)  
 空間インデックス、テセレーション、テセレーション スキームについて説明します。  
  
  
