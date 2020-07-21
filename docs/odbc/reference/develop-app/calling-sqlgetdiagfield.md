---
title: SQLGetDiagField | を呼び出していますMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a097cbdd74cfcd76d2b102bb71dfccb974906709
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306263"
---
# <a name="calling-sqlgetdiagfield"></a>SQLGetDiagField の呼び出し
*Odbc 2.x アプリケーションが*odbc 2.x ドライバーで**SQLGetDiagField**を呼び出すと、ドライバーは、 *DiagIdentifier*引数が SQL_DIAG_CLASS_ORIGIN、SQL_DIAG_CLASS_SUBCLASS_ORIGIN、SQL_DIAG_CONNECTION_NAME、SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE、SQL_DIAG_NUMBER、SQL_DIAG_RETURNCODE、SQL_DIAG_SERVER_NAME、または SQL_DIAG_SQLSTATE の場合に、SQL_SUCCESS と、 * \*DiagInfoPtr*内の適切な情報を返し*ます。* その他のすべての診断フィールドは SQL_ERROR を返します。
