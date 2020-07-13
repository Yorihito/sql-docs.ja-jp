---
title: パブリケーション アクセス リストのログインの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85009906"
---
# <a name="manage-logins-in-the-publication-access-list"></a>パブリケーション アクセス リストのログインの管理
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パブリケーション アクセス リストのログインを管理する方法について説明します。 パブリケーションへのアクセスは、パブリケーション アクセス リスト (PAL) によって制御されます。 ログインおよびグループの PAL への追加および PAL からの削除を実行できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
-   **パブリケーション アクセス リストのログインを管理するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> 前提条件  
  
-   PAL にログインを追加する前に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインをパブリケーション データベースのデータベース ユーザーに関連付ける必要があります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 [パブリケーションの**プロパティ- \<Publication> ** ] ダイアログボックスの [パブリケーション**アクセスリスト**] ページでパブリケーションアクセスリスト (PAL) を使用して、ログインを管理します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../publish/view-and-modify-publication-properties.md)」を参照してください。  
  
#### <a name="to-manage-logins-in-the-pal"></a>PAL のログインを管理するには  
  
1.  [**パブリケーションのプロパティ \<Publication> -** ] ダイアログボックスの [**パブリケーションアクセスリスト**] ページで、[**追加**]、[**削除**]、[**すべて削除**] の各ボタンを使用して、PAL からのログインとグループの追加と削除を行います。 PAL から **distributor_admin** を削除しないでください。 このアカウントはレプリケーションで使用されます。  
  
    > [!NOTE]  
    >  リモート ディストリビューターを使用する場合、PAL 内のアカウントは、パブリッシャーとディストリビューターの両方で使用できる必要があります。 このアカウントは、どちらのサーバーでも定義されているドメイン アカウントまたはローカル アカウントにする必要があります。 両方のログインに関連付けられているパスワードは、同じにする必要があります。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a>PAL に登録されているグループおよびログインを表示するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)を実行します。 [ ** \@ パブリケーション**] では、パブリケーション名を指定します。 これで、PAL のグループおよびログインに関する情報が表示されます。  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a>グループおよびログインを PAL に追加するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)を実行します。 [ ** \@ パブリケーション**] にはパブリケーション名を指定し、[ ** \@ ログイン**] には追加するログインまたはグループの名前を指定します。  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a>グループおよびログインを PAL から削除するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)を実行します。 [ ** \@ パブリケーション**] にはパブリケーション名を指定し、[ ** \@ ログイン**] には削除するログインまたはグループの名前を指定します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションエージェントのセキュリティモデル](replication-agent-security-model.md)   
 [レプリケーショントポロジをセキュリティで保護する](view-and-modify-replication-security-settings.md)   
 [パブリッシャーのセキュリティ保護](secure-the-publisher.md)  
  
  
