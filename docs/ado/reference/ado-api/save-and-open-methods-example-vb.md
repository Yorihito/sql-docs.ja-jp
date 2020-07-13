---
title: Save および Open メソッドの例 (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
author: rothja
ms.author: jroth
ms.openlocfilehash: 37237094c3778fad9c45a2ccad3eebdce02a62bc
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755926"
---
# <a name="save-and-open-methods-example-vb"></a>Save および Open メソッドの例 (VB)
次の3つの例は、 [Save](../../../ado/reference/ado-api/save-method.md)メソッドと[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドを一緒に使用する方法を示しています。  
  
 データベースからテーブルを使用して、事業旅行を行っているとします。 前に、データを[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)としてアクセスし、転送可能な形式で保存します。 宛先に到達すると、**レコードセット**にローカルの切断された**レコードセット**としてアクセスします。 **レコードセット**に変更を加え、再度保存します。 最後に、home を返したときに、もう一度データベースに接続し、その時点で行った変更を反映して更新します。  
  
 まず、 ***Authors***テーブルにアクセスして保存します。  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 この時点で、宛先に到達しました。 ***Authors***テーブルには、ローカルの接続されていない**レコードセット**としてアクセスします。 保存したファイルにアクセスするために使用しているコンピューターには、 **Mspersist**プロバイダーが必要です。 a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 最後に、[ホーム] を返します。 次に、変更を使用してデータベースを更新します。  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [レコードセットの永続性の詳細](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
