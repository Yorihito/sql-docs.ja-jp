---
description: View オブジェクト (ADOX)
title: View オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cc635db04358417948e709a4c47605fae17669b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439364"
---
# <a name="view-object-adox"></a>View オブジェクト (ADOX)
フィルター処理されたレコードセットまたは仮想テーブルを表します。 ADO [コマンド](../../../ado/reference/ado-api/command-object-ado.md) オブジェクトと組み合わせて使用すると、ビュー **オブジェクトを使用して** 、ビューの追加、削除、または変更を行うことができます。  
  
## <a name="remarks"></a>解説  
 ビューは、他のデータベーステーブルまたはビューから作成された仮想テーブルです。 **ビュー**オブジェクトを使用すると、プロバイダーの "create View" 構文を知らない場合や使用しなくても、ビューを作成できます。  
  
 **View**オブジェクトのプロパティを使用すると、次のことができます。  
  
-   [Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してビューを識別します。  
  
-   [コマンド](../../../ado/reference/adox-api/command-property-adox.md)プロパティを使用してビューを追加、削除、または変更するために使用できる ADO**コマンド**オブジェクトを指定します。  
  
-   [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md)プロパティと[DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md)プロパティを使用して日付情報を返します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [View オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Views および Fields コレクションの例 (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views Append メソッドの例 (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views Collection、CommandText プロパティの例 (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views Delete メソッドの例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
