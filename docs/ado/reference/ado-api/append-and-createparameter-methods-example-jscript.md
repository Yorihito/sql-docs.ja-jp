---
description: Append および CreateParameter メソッドの例 (JScript)
title: Append および CreateParameter メソッドの例 (JScript) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- CreateParameter method [ADO], JScript example
- Append method [ADO], JScript example
ms.assetid: 37000833-68f4-45f1-b2dd-7f75893d09d9
author: rothja
ms.author: jroth
ms.openlocfilehash: c0701577bbd569e1b7c01239bd3613591864696d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451304"
---
# <a name="append-and-createparameter-methods-example-jscript"></a>Append および CreateParameter メソッドの例 (JScript)
この例では、 [Append](../../../ado/reference/ado-api/append-method-ado.md) および [createparameter](../../../ado/reference/ado-api/createparameter-method-ado.md) メソッドを使用して、入力パラメーターを使用してストアドプロシージャを実行します。 次のコードを切り取ってメモ帳または別のテキストエディターに貼り付け、 **Appendjs**として保存します。  
  
```  
<!-- BeginAppendJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
<head>  
    <title>Append and CreateParameter Methods Example (JScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>Append and CreateParameter Methods Example (JScript)</h1>  
<%  
    // verify user-input   
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));  
    if (iRoyalty > -1)  
    {  
  
        // connection, recordset and command variables  
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='pubs';Integrated Security='SSPI';";  
        var Cnxn = Server.CreateObject("ADODB.Connection");  
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");  
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");  
        var rsAuthor = Server.CreateObject("ADODB.Recordset");  
        // display variables  
        var strMessage;  
  
        try  
        {  
            // open connection and set cursor location  
            Cnxn.Open(strCnxn);  
            Cnxn.CursorLocation = adUseClient;  
  
            // command object initial parameters  
            cmdByRoyalty.CommandText = "byroyalty";  
            cmdByRoyalty.CommandType = adCmdStoredProc;  
  
            // create the new parameter and append to  
            // the Command object's parameters collection  
            var prmByRoyalty = cmdByRoyalty.CreateParameter("percentage", adInteger, adParamInput);  
            cmdByRoyalty.Parameters.Append(prmByRoyalty);  
            prmByRoyalty.Value = iRoyalty;  
  
            cmdByRoyalty.ActiveConnection = Cnxn;  
  
            // execute command  
            rsByRoyalty = cmdByRoyalty.Execute();  
  
            // display results  
            rsAuthor.Open("Authors", Cnxn);  
  
            while (!rsByRoyalty.EOF)  
            {  
                rsAuthor.Filter = "au_id='" + rsByRoyalty.Fields("au_id") + "'";  
  
                // start new line  
                strMessage = "<P>";  
  
                // recordset data  
                strMessage += rsAuthor.Fields("au_fname") + " ";   
                strMessage += rsAuthor.Fields("au_lname") + " ";  
  
                // end the line  
                strMessage += "</P>";  
  
                // show result  
                Response.Write(strMessage);  
  
                // et next record  
                rsByRoyalty.MoveNext;  
            }  
        }  
        catch (e)  
        {  
            Response.Write(e.message);  
        }  
        finally  
        {  
            // clean up  
            if (rsByRoyalty.State == adStateOpen)  
                rsByRoyalty.Close;  
            if (rsAuthor.State == adStateOpen)  
                rsAuthor.Close;  
            if (Cnxn.State == adStateOpen)  
                Cnxn.Close;  
            rsByRoyalty = null;  
            rsAuthor = null;  
            Cnxn = null;  
        }  
    }  
%>  
  
<hr>  
  
<form method="POST" action="AppendJS.asp" id=form1 name=form1>  
  <p align="left">Enter royalty percentage to find (e.g., 40): <input type="text" name="RoyaltyValue" size="5"></p>  
  <p align="left"><input type="submit" value="Submit" name="B1"><input type="reset" value="Reset" name="B2"></p>  
</form>  
  
</body>  
  
</html>  
<!-- EndAppendJS -->  
```  
  
## <a name="see-also"></a>参照  
 [Append メソッド (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [CreateParameter メソッド (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)
