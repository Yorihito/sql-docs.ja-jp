---
title: updateBlob メソッド (int, java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d0263018-d326-4a7b-bf6f-5f508db899d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117f13d061641d3d9c02e5dbe23c6122c03d1c03
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903471"
---
# <a name="updateblob-method-int-javaioinputstream"></a>updateBlob (int, java.io.InputStream) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された入力ストリームを使用して、指定された列を更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBlob(int columnIndex,  
                       java.io.InputStream inputStream)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
 *inputStream*  
  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateBlob メソッドは、java.sql.ResultSet インターフェイスの updateBlob メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [updateBlob メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
