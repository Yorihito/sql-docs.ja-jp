---
title: SQLGetInfo (Paradox ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Paradox Driver
ms.assetid: 43aab762-68f4-4128-b8f5-8878ea5f1258
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 354fa7f08797ee1fbfb057bfc2f2c192a8c5eddc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298572"
---
# <a name="sqlgetinfo-paradox-driver"></a>SQLGetInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLGetInfo**では、SQL_FILE_USAGE 情報の種類がサポートされています。 返される値は、ドライバーがデータソース内のファイルを直接扱う方法を示す16ビット整数です。  
  
-   SQL_FILE_NOT_SUPPORTED-ドライバーが単一層のドライバーではありません。  
  
-   SQL_FILE_TABLE-1 層ドライバーは、データソース内のファイルをテーブルとして扱います。  
  
-   SQL_FILE_QUALIFIER-1 層ドライバーは、データソース内のファイルを修飾子として扱います。  
  
 ODBC ドライバーは、各ファイルがテーブルであるため SQL_FILE_TABLE を返します。  
  
## <a name="sql_alter_table"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &#124; SQL_AT_DROP_COLUMN  
  
## <a name="sql_ddl_index"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|ドライバー|バージョン|バージョン番号の形式|  
|----------|-------------|-------------------------------|  
|Paradox|3.x|03.00.0000|  
||4.x|04.00.0000|  
||notes|05.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
