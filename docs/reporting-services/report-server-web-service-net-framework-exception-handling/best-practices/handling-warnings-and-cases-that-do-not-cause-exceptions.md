---
title: 例外が発生しない警告および状況の処理 | Microsoft Docs
description: 適切なアクションを実行できるように、例外を発生させない警告とケースを処理する方法について説明します。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5dd1c9335db348aeb3cb979079d3f1bd929f008a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216391"
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a>例外が発生しない警告および状況の処理
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、警告および特定のエラーに対して例外をスローしません。 たとえば、<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> メソッドを使用して新しいレポートをレポート サーバーにパブリッシュしたときに警告が発生した場合、その警告は <xref:ReportService2010.Warning> オブジェクトの配列として返されます。 それらの警告は、適切な処置を実行できるように処理および表示する必要があります。  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 もう 1 つのエラー処理方法は、特定のメソッドの戻り値を評価することです。 たとえば、<xref:ReportService2010.ReportingService2010.FindItems%2A> メソッドを使用して、レポート サーバー データベースの特定のアイテムを検索できます。 検索条件に一致するアイテムが見つからない場合、<xref:ReportService2010.CatalogItem> オブジェクトの null 配列が返されます。 その配列を評価し、**null** を調べて、アイテムが見つからなかった場合はユーザーに知らせる必要があります。  
  
## <a name="see-also"></a>参照  
 <xref:ReportService2010.CatalogItem>   
 [Reporting Services における例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
