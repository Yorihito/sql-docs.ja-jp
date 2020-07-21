---
title: スレッドサポート (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2aa19eb233525b5a65ef67fe9903814fc1163177
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303083"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>スレッド サポート (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーはスレッドセーフです。 環境ハンドル (*h)*) へのアクセス、接続ハンドル (*hdbc*)、およびステートメントハンドル (*hstmt*) が適切なセマフォにラップされ、他のプロセスがにアクセスしたり、ドライバーの内部データ構造を変更したりするのを防ぐことができます。  
  
 マルチスレッドアプリケーションでは、別のスレッドで[SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)を呼び出すことによって、 *hstmt*で同期的に実行されている関数を取り消すことができます。  
  
 ドライバーは、プログレッシブフェッチを使用するときに、別のスレッドを使用してデータをフェッチします。 データソースに対してプログレッシブフェッチを使用するには、[ [ODBC Visual FoxPro セットアップ] ダイアログボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)の [**バックグラウンドでデータをフェッチ**する] チェックボックスをオンにするか、または、接続文字列で backgroundfetch attribute キーワードを使用します。 マルチスレッドアプリケーションからドライバーを呼び出すときは、バックグラウンドフェッチを使用しないようにしてください。 接続文字列の属性キーワードの詳細については、「[接続文字列の使用](../../odbc/microsoft/using-connection-strings.md)」を参照してください。  
  
 スレッドと**SQLCancel**の詳細については、「 [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) In the *ODBC プログラマーズリファレンス*」を参照してください。
