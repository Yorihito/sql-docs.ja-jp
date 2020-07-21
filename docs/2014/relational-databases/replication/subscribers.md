---
title: '[サブスクライバー] | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff5492a10f42aa83b2756ba55ec861eeb9bde6bd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047630"
---
# <a name="subscribers"></a>[サブスクライバー]
  選択した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリケーションへのサブスクリプションを受け取るサブスクライバーまたは以外のサブスクライバーを指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
## <a name="options"></a>オプション  
 **[パブリッシャーのプロパティ]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [パブリケーション][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで選択したパブリケーションへのサブスクライバーとして、 **のデータ ソースまたは** 以外のデータ ソースを有効にするには、グリッド内の対応するチェック ボックスをオンにします。 サブスクライバーが一覧にない場合、 **[サブスクライバーの追加]** または **[SQL Server サブスクライバーの追加]** をクリックします。  
  
 **サブスクリプション データベース**  
 この列で表示される情報と実行できる操作は、 **[サブスクライバー]** 列に表示されているサブスクライバーの種類によって変わります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合、 **[サブスクリプション データベース]** の一覧からサブスクリプション データベースを選択するか、同じ一覧から **[新しいデータベース]** コマンドを選択して新しいデータベースを作成します。  
  
    > [!NOTE]  
    >  パブリッシャーをサブスクライバーとして有効にする場合、サブスクリプション データベースはパブリケーション データベースとは別にする必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーの場合、サブスクリプション データベースは表示されません。 **[SQL Server 以外のサブスクライバーの追加]** ダイアログ ボックスの **[データ ソース名]** フィールドで、データベースおよび他の接続情報を指定します。 このダイアログ ボックスを開くには、 **[サブスクライバーの追加]** をクリックして **[SQL Server 以外のサブスクライバーの追加]** をクリックします。  
  
 **[サブスクライバーの追加]**  
 サブスクライバーとして有効にできるサーバーの一覧に、サーバーを追加します。 このボタンは、次に示す条件がすべて満たされた場合に表示されます。  
  
-   選択したパブリケーションが、サブスクリプションの更新をサポートしないスナップショット パブリケーションまたはトランザクション パブリケーションである。  
  
    > [!NOTE]  
    >  サブスクライブしているパブリケーションに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクリプションが含まれており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーにまだ対応していない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクリプションを追加できません。  
  
-   サブスクリプションがプッシュ サブスクリプションである。  
  
-   選択したパブリケーションのパブリッシャーが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンである。  
  
 **[サブスクライバーの追加]** をクリックすると、 **[SQL Server サブスクライバーの追加]** と **[SQL Server 以外のサブスクライバーの追加]** という 2 つの選択肢を持つメニューが表示されます。 Oracle または IBM DB2 のサブスクライバーを追加するには、 **[SQL Server 以外のサブスクライバーの追加]** をクリックします。  
  
 **[SQL Server サブスクライバーの追加]**  
 サブスクライバーとして有効にできるサーバーの一覧に、サーバーを追加します。 このボタンは、次のいずれかの条件が満たされた場合に表示されます。  
  
-   選択したパブリケーションが、サブスクリプションの更新をサポートするマージ パブリケーション、スナップショット パブリケーション、またはトランザクション パブリケーションである。  
  
-   サブスクリプションがプル サブスクリプションである。  
  
-   選択したパブリケーションのパブリッシャーが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]よりも古いバージョンである。 古いバージョンの場合、このボタンは次の条件のいずれかが満たされた場合にのみ表示されます。  
  
    -   パブリッシャーの **sysadmin** 固定サーバー ロールのメンバーである。  
  
    -   サブスクライバーが、 **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[サブスクライバー]** ページに追加されている。  
  
    -   パブリケーションで匿名サブスクリプションが許可されている。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [ssSDSFull](create-a-push-subscription.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
