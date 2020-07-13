---
title: 記述子フィールドの値を取得する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 43467d19f3f2e576efa0402c4ba513e23da59390
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304323"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>記述子フィールドの値の取得
アプリケーションは**SQLGetDescField**を呼び出すことで、記述子レコードの1つのフィールドを取得できます。 **SQLGetDescField**では、ODBC で定義されているすべての記述子フィールドとドライバー定義フィールドへのアクセスがアプリケーションに与えられます。  
  
 **Sqlgetdescrec**を呼び出して、列またはパラメーターのデータのデータ型とストレージに影響を与える複数の記述子フィールドの設定を取得できます。
