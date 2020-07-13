---
title: Columns コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
author: rothja
ms.author: jroth
ms.openlocfilehash: 46168e694f87c4a8a827420f8b395b843da1d29b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759338"
---
# <a name="columns-collection-adox"></a>Columns コレクション (ADOX)
テーブル、インデックス、またはキーのすべての[Column](../../../ado/reference/adox-api/column-object-adox.md)オブジェクトを格納します。  
  
## <a name="remarks"></a>解説  
 **Columns**コレクションの[Append](../../../ado/reference/adox-api/append-method-adox-columns.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   **追加**メソッドを使用して、新しい列をコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [Item](../../../ado/reference/ado-api/item-property-ado.md)プロパティを使用して、コレクション内の列にアクセスします。  
  
-   [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、コレクションに含まれる列の数を返します。  
  
-   [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドを使用して、コレクションから列を削除します。  
  
-   [更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベースのスキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
> [!NOTE]
>  [テーブル](../../../ado/reference/adox-api/tables-collection-adox.md)コレクションに既に追加されている[テーブル](../../../ado/reference/adox-api/table-object-adox.md)**に列が**存在しない場合、[インデックス](../../../ado/reference/adox-api/index-object-adox.md)の**Columns**コレクションに**列**を追加すると、エラーが発生します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Columns コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Columns および Tables Append メソッド、Name プロパティの例 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close メソッド、Table Type プロパティの例 (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [順序のプロパティの例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
