---
title: SQL Mail ではなくデータベース メールを使用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6a957b65975645bdeb9f55faee4e650b53718b8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047752"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>SQL Mail ではなくデータベース メールを使用する
  このルールでは、sys.configurations カタログ ビューを確認して、サーバー全体に適用される構成オプションである SQL Mail XPs が ON に設定されているかどうかを調べます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 SQL Mail は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の将来のバージョンで削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 メールを送信するには、データベース メールを使用してください。  
  
 SQL Mail は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対してインプロセスで実行されます。 SQL Mail がダウンした場合、サーバーもダウンします。 データベース メールは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部の別個のプロセスで実行され、スケーラブルです。拡張 MAPI クライアント コンポーネントを実稼働サーバーにインストールする必要はありません。  
  
## <a name="for-more-information"></a>詳細情報  
 [データベース メール](../database-mail/database-mail.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
