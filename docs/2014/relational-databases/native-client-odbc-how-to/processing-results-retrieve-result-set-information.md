---
title: 結果セットの情報の取得 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048206"
---
# <a name="retrieve-result-set-information-odbc"></a>結果セットの情報の取得 (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>結果セットに関する情報を取得するには  
  
1.  [Sqlnumresultcols](../native-client-odbc-api/sqlnumresultcols.md)を呼び出して、結果セット内の列の数を取得します。  
  
2.  結果セット内の各列に対して次の操作を行います。  
  
    -   [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)を呼び出して、結果列に関する情報を取得します。  
  
     または  
  
    -   [Sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md)を呼び出して、結果列に関する特定の記述子情報を取得します。  
  
## <a name="see-also"></a>参照  
 [結果の処理方法に関するトピック &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [ODBC&#41;&#40;結果セットの特性の決定](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
