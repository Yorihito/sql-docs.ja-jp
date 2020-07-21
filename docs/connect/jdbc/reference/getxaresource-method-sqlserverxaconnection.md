---
title: getXAResource メソッド (SQLServerXAConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3d4b2132c3bbcf5612faa5f319a5358f158e2b7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977978"
---
# <a name="getxaresource-method-sqlserverxaconnection"></a>getXAResource メソッド (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) オブジェクトの分散トランザクションへの参加を管理するため、トランザクション マネージャーが使用する [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>戻り値  
 XAResource オブジェクト。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この getXAResource メソッドは、javax.sql.XAConnection インターフェイスの getXAResource メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAConnection のメソッド](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [SQLServerXAConnection のメンバー](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [SQLServerXAConnection クラス](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
