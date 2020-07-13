---
title: ASP.NET における入れ子になった FOR XML クエリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], ASP.NET and
- nested FOR XML queries in ASP.NET
- ASP.NET [SQL Server]
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
author: rothja
ms.author: jroth
ms.openlocfilehash: c5f267db5449741fa1e70b4a4d51b33be45178af
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85046468"
---
# <a name="use-nested-for-xml-queries-in-aspnet"></a>ASP.NET における入れ子になった FOR XML クエリの使用
  この例では、ASP.NET アプリケーションで SQL Server のストアド プロシージャを実行してブラウザーに XML を返します。 このストアド プロシージャは、入れ子になったクエリを使用して XML を生成します。 同様の SELECT ステートメントは、「 [入れ子構造で AUTO モードのクエリを使用した兄弟の生成](generate-siblings-with-a-nested-auto-mode-query.md)」でも見ることができます。 この例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で入れ子になった FOR XML クエリを使用して要素中心の XML を生成する方法の一例を示しています。  
  
## <a name="example"></a>例  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 次に .aspx アプリケーションを示します。 これによってストアド プロシージャが実行され、XML がブラウザーに返されます。  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースにストアド プロシージャを作成します。  
  
2.  .aspx アプリケーションを c:\inetpub\wwwroot directory に保存します (GetSalesOrderInfo.aspx)。  
  
3.  アプリケーションを実行します (「」を実行 http://server/GetSalesOrderInfo.aspx) します。  
  
## <a name="see-also"></a>参照  
 [入れ子になった FOR XML クエリの使用](use-nested-for-xml-queries.md)  
  
  
