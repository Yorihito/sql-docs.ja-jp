---
title: SQL ステートメントの相互運用性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3d7a76c67096d2e76fe1cd3d4b15f73122699e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302803"
---
# <a name="interoperability-of-sql-statements"></a>SQL ステートメントの相互運用性
アプリケーションの他の部分と同様に、SQL ステートメントを相互運用可能または DBMS 固有にすることができます。 アプリケーションの他の部分と同様に、相互運用可能な SQL ステートメントの方法はアプリケーションの種類によって異なります。 カスタムアプリケーションは、通常、1つまたは2つの Dbms の機能を利用するように設計されているため、相互運用可能な SQL ステートメントを使用することはあまりありません。 汎用アプリケーションは、さまざまな Dbms で動作するように設計されているため、相互運用可能な SQL ステートメントを使用します。 また、垂直方向のアプリケーションは、通常、特定のレベルの機能を要求し、それ以外の場合は相互運用可能な SQL ステートメントを使用して、一定の場所にあります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL 文法の選択](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [相互運用可能な SQL ステートメントの構築](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
