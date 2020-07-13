---
title: 格納されている XML スキーマ コレクションの表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef32368031876bc14619cd14aa215402c67618b6
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80662922"
---
# <a name="view-a-stored-xml-schema-collection"></a>格納されている XML スキーマ コレクションの表示
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)を使用して XML スキーマ コレクションをインポートすると、メタデータにスキーマ コンポーネントが格納されます。 固有の関数 [xml_schema_namespace](../../t-sql/xml/xml-schema-namespace.md)を使用して、XML スキーマ コレクションを再構築できます。 この関数は、 **xml** データ型のインスタンスを返します。  
  
 たとえば、次のクエリでは、`ProductDescriptionSchemaCollection`データベースの実稼働リレーショナル スキーマから XML スキーマ コレクション ( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ) が取得されます。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 XML スキーマ コレクションに含まれるスキーマを 1 つだけ表示するには、 **によって返された** xml `xml_schema_namespace`型の結果に対して XQuery を指定します。  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 たとえば、次のクエリでは、 `ProductDescriptionSchemaCollection` XML スキーマ コレクションに含まれる、製品保証書とメンテナンスの XML スキーマ情報を取得しています。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 次のクエリに示すように、省略可能な対象名前空間を 3 番目のパラメーターとして `xml_schema_namespace` 関数に渡すことにより、特定のスキーマをコレクションから取得することもできます。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 CREATE XML SCHEMA COLLECTION を使用してデータベースに XML スキーマ コレクションを作成すると、スキーマ コンポーネントがメタデータに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が理解したスキーマ コンポーネントのみが格納されることに注意してください。 コメント、注釈、または XSD 以外の属性は格納されません。 したがって、 **xml_schema_namespace** によって再構築されたスキーマは、機能的には元のスキーマと同じですが、同じように見えるとは限りません。 たとえば、元のスキーマにあったものと同じプレフィックスはありません。 **xml_schema_namespace** によって返されるスキーマでは、対象名前空間のプレフィックスとして **t** が使用され、他の名前空間には **ns1**、 **ns2**などが使用されています。  
  
 XML スキーマの同一のコピーを保持するには、ファイルまたはデータベース テーブルの **xml** 型の列に XML スキーマを保存する必要があります。  
  
 [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) カタログ ビューでも、XML スキーマ コレクションに関する情報が返されます。 この情報には、コレクションの名前、作成日、およびコレクションの所有者が含まれます。  
  
## <a name="see-also"></a>参照  
 [XML スキーマ コレクション &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
