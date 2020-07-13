---
title: 'ジョブのプロパティ: [新しいジョブ] ([通知] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8fafac7faaf98fd8cf9bd3b0bf772dc77324bae
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062275"
---
# <a name="job-properties-new-job-notifications-page"></a>[ジョブのプロパティ]:[新しいジョブ] ([通知] ページ)
  このページを使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、ジョブの完了時にエージェントが実行するアクションを設定できます。  
  
## <a name="options"></a>オプション  
 **メッセージ**  
 このオプションを選択すると、ジョブの完了時に電子メールが送信されます。 このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から選択します。  
  
 **ページ**  
 このオプションを選択すると、ジョブの完了時にオペレーターのポケットベルに電子メールが送信されます。 このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から指定します。  
  
 **Net send**  
 このオプションを選択すると、ジョブの完了時に Net Send を使用してオペレーターに通知が送られます。 このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から指定します。  
  
 **[Windows アプリケーション イベント ログに書き込む]**  
 このオプションを選択すると、ジョブの完了時にアプリケーション イベント ログにエントリが書き込まれます。 このオプションを選択した後、エントリの書き込みを実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から選択します。  
  
 **[自動的にジョブを削除]**  
 このオプションを選択すると、ジョブの完了時にジョブが削除されます。 このオプションを選択した後、ジョブの削除を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]** の中から選択します。  
  
## <a name="see-also"></a>参照  
 [ジョブの実装](implement-jobs.md)   
 [データベース メールを使用するように SQL Server エージェント メールを構成する](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
