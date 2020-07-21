---
title: Dbms | でのトランザクションのサポートMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6da6fdc819d8852aadcd7b672ef06e99d46c0ea
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298007"
---
# <a name="transaction-support-in-dbmss"></a>DBMS でのトランザクションのサポート
一部のデータベース (特に、dBASE、Paradox、および Btrieve などのデスクトップデータベース) では、トランザクションはサポートされていません。 トランザクションをサポートするデータベース間でも、トランザクション内で使用できる SQL ステートメントの種類には違いがあります。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明の SQL_TXN_CAPABLE オプションを参照してください。
