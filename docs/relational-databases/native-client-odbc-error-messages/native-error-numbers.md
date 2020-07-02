---
title: ネイティブエラー番号 |Microsoft Docs
description: エラーの場合、SQL Server Native Client ODBC ドライバーは、SQL Server またはドライバーによって検出されたエラー (0) からネイティブエラー番号を返します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39ad8865ce8af576481717f50b9a8cfc42fe4945
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774321"
---
# <a name="native-error-numbers"></a>ネイティブ エラー番号
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  データソースで発生したエラー (によって返される) の場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーは、によって返されたネイティブエラー番号を返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 ドライバーによって検出されたエラーの場合、native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLIENT ODBC ドライバーは、ネイティブエラー番号0を返します。 ネイティブエラー番号の一覧の詳細については、の**master**データベースにある**sysmessages**システムテーブルの error 列を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
 状態エラーコードの詳細については、「 [SQLSTATE &#40;ODBC エラーコード&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)」を参照してください。 Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。  
  
## <a name="see-also"></a>関連項目  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
