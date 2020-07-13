---
title: SQL Server テーブルからの列の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: rothja
ms.author: jroth
ms.openlocfilehash: d416514ed627556b1716fba2ee4be8861fdabad2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017849"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>SQL Server テーブルからの列の削除
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Itabledefinition::D ropcolumn**関数を公開します。 コンシューマーはこの関数を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルから列を削除できます。  
  
 コンシューマーはテーブル名は、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
 列名は *pColumnID* パラメーターの *uName* 共用体の *pwszName* メンバーに指定します。 列名は Unicode 文字列で指定します。 *pColumnID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](tables-and-indexes.md)  
  
  
