---
title: CLR データベースオブジェクトからのデータアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: d229d490a9f3a7bc6f613259ee0535218de47975
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970648"
---
# <a name="data-access-from-clr-database-objects"></a>CLR データベース オブジェクトからのデータ アクセス
  共通言語ランタイム (CLR) ルーチンは、 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] リモートインスタンスに格納されているデータだけでなく、実行されるのインスタンスに格納されているデータにも簡単にアクセスできます。 ルーチンからどのデータにアクセスできるかは、コードが実行されているユーザー コンテキストによって決まります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]マネージクライアントおよび中間層アプリケーションからのデータに対して .NET Framework Data Provider を使用して、CLR データベースオブジェクト内からデータにアクセスします。 このため、クライアント アプリケーションや中間層アプリケーションでは、ADO.NET と `SqlClient` の知識を活用できます。  
  
> [!NOTE]  
>  ユーザー定義型メソッドとユーザー定義関数では、既定ではデータ アクセスの実行が許可されていません。 UDT (ユーザー定義型) メソッドやユーザー定義関数からの読み取り専用データ アクセスを可能にするには、`DataAccess` または `SqlMethodAttribute` の `SqlFunctionAttribute` プロパティを `DataAccessKind.Read` に設定する必要があります。 UDT またはユーザー定義関数によるデータ変更操作は許可されません。この操作を実行しようとすると、実行時に例外がスローされます。  
  
 ここでは、CLR データベース オブジェクト内からデータにアクセスする際の機能や動作の具体的な違いについて説明します。 ADO.NET の機能の詳細については、.NET Framework SDK に付属の ADO.NET のドキュメントを参照してください。  
  
 次の表に、このセクションの各トピックの一覧を示します。  
  
 [コンテキスト接続](context-connection.md)  
 SQL Server へのコンテキスト接続について説明します。  
  
 [接続の権限借用と資格情報](impersonation-and-credentials-for-connections.md)  
 接続の権限借用および接続の資格情報について説明します。  
  
 [ADO.NET に対する SQL Server インプロセス固有の拡張機能](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 プロセス内の固有の `SqlPipe`、`SqlContext`、`SqlTriggerContext`、および `SqlDataRecord` の各オブジェクトについて説明します。  
  
 [CLR 統合とトランザクション](../../native-client-ole-db-transactions/transactions.md)  
 System.Transactions 名前空間で提供される新しいトランザクション フレームワークを ADO.NET および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 統合と統合する方法について説明します。  
  
 [CLR データベース オブジェクトからの XML シリアル化](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で CLR データベース オブジェクトの XML シリアル化のシナリオを有効にする方法について説明します。  
  
  
