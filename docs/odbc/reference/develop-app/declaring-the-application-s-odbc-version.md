---
title: Application&#39;s ODBC バージョン | を宣言していますMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba346ed7f7a261446110c5513026d20a86fd3a19
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285232"
---
# <a name="declaring-the-application39s-odbc-version"></a>Application&#39;s ODBC バージョンを宣言しています
アプリケーションで接続を割り当てる前に、SQL_ATTR_ODBC_VERSION 環境属性を設定する必要があります。 この属性は、次の項目を使用する場合に、アプリケーション*が odbc* *2.X または*odbc 3.x の仕様に従っていることを示します。  
  
-   **Sqlstates**。 ODBC *2.x と odbc* *3. x*では、多くの SQLSTATE 値が異なります。  
  
-   **日付、時刻、およびタイムスタンプの型識別子**。 次の表は、ODBC *2.x および odbc* *3. x*の日付、時刻、およびタイムスタンプデータの型識別子を示しています。  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**SQL の型識別子**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C 型識別子**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_**Sqltables の CatalogName 引数**。   *ODBC 2.x では、* *CatalogName*引数のワイルドカード文字 ("%" と "_") は文字どおりに扱われます。 ODBC 3.x では、ワイルドカード文字として扱わ*れます。* したがって *、ODBC 2.x*仕様に従うアプリケーションでは、これらをワイルドカード文字として使用することはできません。また、リテラルとして使用する場合はエスケープされません。 ODBC 3.x 仕様に従うアプリケーションでは、これらをワイルドカード文字として使用したり、エスケープしてリテラルとして使用したりでき*ます。* 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 ODBC 3.x*ドライバーマネージャーおよび odbc* *3.x ドライバーは*、アプリケーションが記述されている odbc 仕様のバージョンを確認し、それに応じて応答します。 たとえば、アプリケーションが ODBC *2.x 仕様に*従っていて、 **SQLPrepare**を呼び出す前に**sqlexecute**を呼び出すと、Odbc *3.X ドライバーマネージャー*は SQLSTATE S1010 (関数シーケンスエラー) を返します。 アプリケーションが ODBC *3. x*仕様に準拠している場合、ドライバーマネージャーは SQLSTATE HY010 (関数シーケンスエラー) を返します。 詳細については、「[旧バージョンとの互換性と標準の準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。  
  
> [!IMPORTANT]  
>  *Odbc 2.x の仕様に*準拠しているアプリケーションでは *、odbc 2.x ドライバーを*使用して*いるときに*odbc 3.x に新しく追加された機能を使用しないようにするために、条件付きコードを使用する必要があります。 Odbc *2.x ドライバーは* *、odbc 3.x 仕様に*従っていることをアプリケーションが宣言するため *、odbc 3.x*の新機能をサポートしていません。 さらに、 *odbc 3.x ドライバーは* *、odbc 2.x の仕様に*従っていることをアプリケーションが宣言するため、odbc 3.x の新機能のサポートを停止しません *。*
