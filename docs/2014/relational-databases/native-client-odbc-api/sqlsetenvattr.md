---
title: SQLSetEnvAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: rothja
ms.author: jroth
ms.openlocfilehash: f0dbd4d01de9ca769c46a93f810f0149f5b86981
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021598"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
  Odbc[プログラマーズリファレンス](https://go.microsoft.com/fwlink/?LinkId=45250)では、odbc ドライバーが odbc 2 に書き込まれたアプリケーションから**SQLSetEnvAttr**属性の仕様を解釈する方法を定義します。*x*または ODBC 3。*x* API。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーは、これらの規則に準拠しています。  
  
 **SQLSetEnvAttr**によって制御される属性の1つは、接続プールを使用するかどうかです。 Native Client ODBC ドライバーで接続プールを使用する場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [SQLDriverConnect](sqldriverconnect.md)または**SQLConnect**を使用して接続するときに、 *drivercompletion*パラメーターを SQL_DRIVER_NOPROMPT に設定する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLSetEnvAttr 関数](https://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
