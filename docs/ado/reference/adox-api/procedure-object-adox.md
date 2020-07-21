---
title: プロシージャオブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4a56088e47a9f794f1862ef87bf142a8d3ab12c4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763693"
---
# <a name="procedure-object-adox"></a>Procedure オブジェクト (ADOX)
ストアドプロシージャを表します。 ADO[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトと共に使用する場合、**プロシージャ**オブジェクトを使用して、ストアドプロシージャの追加、削除、または変更を行うことができます。  
  
## <a name="remarks"></a>解説  
 **プロシージャ**オブジェクトを使用すると、プロバイダーの "create Procedure" 構文を知らない場合や使用しなくても、ストアドプロシージャを作成できます。  
  
 **プロシージャ**オブジェクトのプロパティを使用すると、次の操作を実行できます。  
  
-   [Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してプロシージャを識別します。  
  
-   [Command](../../../ado/reference/adox-api/command-property-adox.md)プロパティを使用してプロシージャを作成または実行するために使用できる ADO**コマンド**オブジェクトを指定します。  
  
-   [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md)プロパティと[DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md)プロパティを使用して日付情報を返します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Procedure オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Command プロパティと CommandText プロパティの例 (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Parameters コレクション、Command プロパティの例 (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Procedures Append メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedures Delete メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
