---
title: SQL Server エージェントログ配布ジョブカテゴリによってアップグレードが失敗するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2f5947e8fc8d459388fe35d86c75666e25b5d907
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036128"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>SQL Server エージェントのログ配布ジョブ カテゴリが原因でアップグレードに失敗する
  "ログ配布" という名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ カテゴリがある場合、アップグレード プロセスは失敗します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 "ログ配布" という名前のシステム ジョブ カテゴリがあります。 アップグレード対象のインストールにユーザーが作成した "ログ配布" という名前のジョブ カテゴリが含まれている場合、アップグレードする前にそのジョブ カテゴリの名前を変更する必要があります。名前を変更しないと、アップグレード プロセスは失敗します。  
  
## <a name="see-also"></a>参照  
 [アップグレード後にログ配布が実行されない](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [アップグレードすると、SQL Server エージェントユーザープロキシアカウントが一時的な UpgradedProxyAccount に変更されます](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
