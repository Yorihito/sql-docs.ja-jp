---
title: テンプレート、XSL、およびスキーマのキャッシュ (SQLXML)
description: SQLXML 4.0 でのテンプレート、XSL、およびスキーマのキャッシュに関する情報を表示します。
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a1481a45c65f2c6876c6acbc35d42d1706776b49
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650499"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>テンプレート、XSL、およびスキーマのキャッシュ (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  パフォーマンス向上のため、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 ではテンプレート、XSL、およびスキーマのキャッシュがサポートされています。  
  
 すべてのスキーマ、テンプレート、および XSL ファイル (https://または ftp://の場所のファイルを除く) はキャッシュされます。 キャッシュされたファイルは処理が実行されている間メモリに残ります。 処理が終了すると、すべてのキャッシュは失われます。 したがって、クエリごとに 1 つの処理を実行する場合は、キャッシュがそれほどメリットにならない場合もあります。  
  
 ここでは、キャッシュの詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テンプレートのキャッシュ &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 テンプレートのキャッシュ用のレジストリ キーについて説明します。  
  
 [XSL キャッシュ &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 XSL のキャッシュ用のレジストリ キーについて説明します。  
  
 [スキーマキャッシュ &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 スキーマのキャッシュに関する SQLXML サイド バイ サイド インストールについて説明し、スキーマのキャッシュ用のレジストリ キーを提供します。  
  
  
