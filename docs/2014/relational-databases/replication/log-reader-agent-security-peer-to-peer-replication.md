---
title: '[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae5c8d56c1d51290c35a04c22474fcc04ddff61d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065913"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション)
  **[ログ リーダー エージェントのセキュリティ]** ページを使用すると、各ピアでログ リーダー エージェントが実行され、接続するときに使用されるアカウントを指定できます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。  
  
> [!NOTE]  
>  トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。 データベースにログ リーダー エージェントが既に設定されている場合 (このウィザードを以前に実行したときのパブリケーション、または同じデータベースにある他のトランザクション パブリケーションで)、使用されている資格情報をこのウィザードで変更することはできません。 新しい資格情報を指定した場合は無視されます。 資格情報を変更するには、 **[パブリケーションのプロパティ]** ダイアログ ボックスを使用します。 詳細については、「[レプリケーションのセキュリティ設定を表示および変更](security/view-and-modify-replication-security-settings.md)する」を参照してください。  
  
## <a name="options"></a>オプション  
 各ピアの行にあるプロパティ ボタン (**[...]**) をクリックすると、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスが開きます。 エージェントで使用されるアカウントに必要な権限の詳細については、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスを開いて **[ヘルプ]** をクリックしてください。  
  
 このダイアログ ボックスに設定値を入力すると、サブスクライバーへの接続情報がグリッドに表示されます。  
  
 **[パブリッシャーのエージェント]**  
 各ピア サーバー インスタンスの名前です。  
  
 **[ピア データベース]**  
 各ピアでパブリケーション データベースおよびサブスクリプション データベースとして機能するデータベースです。  
  
 **[ディストリビューターへの接続]**  
 ディストリビューターに接続するコンテキストを作成します。 ディストリビューターへのローカル接続は、常にエージェントを実行する Windows アカウントのコンテキストを使用して行われる [!INCLUDE[msCoName](../../includes/msconame-md.md)] ため、このフィールドには常に [権限**の借用] ' \<Domain> \\<ログイン \> '** または **' \<Computer> \\<ログイン \> **' が表示されます。  
  
 **[パブリッシャーへの接続]**  
 パブリッシャーへの接続が作成されるときのコンテキストです。 パブリッシャーへの接続は、ログインを使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] か、エージェントを実行する Windows アカウントのコンテキストを使用して行うことができます。 フィールドには次のいずれかが表示されます。 **Use login ' \<Login> '**、 **impersonate ' \<Domain> \\<login \> '** 、または**impersonate ' \<Computer> \\<login \> '**。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [ピアツーピアトポロジの管理 &#40;レプリケーション Transact-sql プログラミング&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [ピアツーピアトランザクションレプリケーション](transactional/peer-to-peer-transactional-replication.md)  
  
  
