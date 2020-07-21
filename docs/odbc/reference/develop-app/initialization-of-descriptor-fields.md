---
title: 記述子フィールドの初期化 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300122"
---
# <a name="initialization-of-descriptor-fields"></a>記述子フィールドの初期化
アプリケーションの行記述子が割り当てられると、そのフィールドには[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)に示されている初期値が与えられます。 SQL_DESC_TYPE フィールドの初期値は SQL_DEFAULT です。 これにより、アプリケーションに表示するためのデータベースデータの標準的な処理が提供されます。 アプリケーションでは、記述子レコードのフィールドを設定することによって、異なるデータ処理を指定できます。  
  
 記述子ヘッダー内の SQL_DESC_ARRAY_SIZE の初期値は1です。 アプリケーションでこのフィールドを変更して、複数行のフェッチを有効にすることができます。  
  
 既定値の概念は、IRD のフィールドでは無効です。 アプリケーションは、準備されたステートメントまたは実行されたステートメントが関連付けられている場合にのみ、IRD のフィールドにアクセスできます。  
  
 IPD の特定のフィールドは、IPD がドライバーによって自動的に設定された後にのみ定義されます。 定義されていない場合は未定義です。 これらのフィールドは、SQL_DESC_CASE_SENSITIVE、SQL_DESC_FIXED_PREC_SCALE、SQL_DESC_TYPE_NAME、SQL_DESC_UNSIGNED、および SQL_DESC_LOCAL_TYPE_NAME です。
