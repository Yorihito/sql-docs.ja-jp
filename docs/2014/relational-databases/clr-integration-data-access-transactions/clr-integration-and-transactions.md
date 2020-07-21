---
title: CLR 統合とトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955068"
---
# <a name="clr-integration-and-transactions"></a>CLR 統合とトランザクション
  `System.Transactions` 名前空間では、ADO.NET と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR (共通言語ランタイム) 統合に完全に統合される新しいトランザクション フレームワークが提供されます。 `System.Transactions` と ADO.NET は連携し、マネージド アプリケーションでのローカル トランザクションや分散トランザクションの用途を拡張および単純化します。  
  
> [!NOTE]  
>  CLR ユーザー定義プロシージャ (UDP) は、このプロシージャが実行されているサーバーへの接続 (ループバック接続) を確立して、同じトランザクションに参加することができません。 この操作を試みると、接続試行がブロックされ、制御は UDP に返されません。 これにより、UDP でタイムアウト エラー (メッセージ 1206) が発生します。  
  
 トランザクションと .NET Framework の詳細については、.NET Framework SDK の「トランザクションの実行」と「トランザクションの利用」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [トランザクションの昇格](transaction-promotion.md)  
 トランザクションを昇格する機能とこの機能の使用方法について説明します。  
  
 [現在のトランザクションへのアクセス](accessing-the-current-transaction.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインプロセスで現在実行中のトランザクションにアクセスする方法について説明します。  
  
 [System.Transactions の使用](../native-client-ole-db-transactions/transactions.md)  
 マネージド アプリケーションでの `System.Transactions` API (アプリケーション プログラミング インターフェイス) の使用方法について説明します。  
  
 [トランザクションの有効期間](transaction-lifetimes.md)  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで開始されたトランザクションと、CLR アプリケーションで開始されたトランザクションの有効期間の違いについて説明します。  
  
## <a name="see-also"></a>参照  
 [CLR データベース オブジェクトからのデータ アクセス](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
