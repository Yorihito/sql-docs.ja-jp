---
title: クライアント側での XML の処理 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: 22c8b5e11ced4cdff95a6cc2d8aeeaa7e25a4d90
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015312"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>クライアント側での XML の処理 (SQLXML マネージド クラス)
  この例は、ClientSideXml プロパティの使用方法を示しています。 サーバーで、アプリケーションによってストアド プロシージャが実行されると、 クライアント側でその結果 (2 列の行セット) が処理され、XML ドキュメントが生成されます。  
  
 次の GetContacts ストアドプロシージャは、AdventureWorks データベースの Person. Contact テーブルにある従業員の**FirstName**と**LastName**を返します。  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 この C# アプリケーションは、ストアドプロシージャを実行し、CommandText 値を指定するために FOR XML AUTO オプションを指定します。 アプリケーションでは、SqlXmlCommand オブジェクトの ClientSideXml プロパティが true に設定されています。 これにより、前から存在するストアド プロシージャを実行して行セットを返すことができ、クライアント側で XML 変換を適用することができます。  
  
> [!NOTE]  
>  コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
 この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。  
  
### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  ストアドプロシージャを作成します。  
  
2.  この例で提供される C# コード (DocSample.cs) をフォルダーに保存します。 コードを編集し、適切なログインおよびパスワード情報を指定します。  
  
3.  コードをコンパイルします。 コマンド プロンプトでコードをコンパイルするには、次を使用します。  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     これにより、実行可能ファイル (DocSample.exe) が作成されます。  
  
4.  コマンド プロンプトで、DocSample.exe を実行します。  
  
  
