---
title: パラメーター化されたクエリの制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: 4edc0566-bba8-42b2-ab0e-60dfb67b5e7b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55a89e2ae0493cca1562b056e21455c6fd09242f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290783"
---
# <a name="parameterized-query-limitations"></a>パラメーター化クエリの制限事項
Microsoft Access ドライバーを使用する場合、パラメーター化されたクエリは、CALL *query-name* [(*parameter*[,*parameter*]...)] という構文を使用して呼び出すことができます。
