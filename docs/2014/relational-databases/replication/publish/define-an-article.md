---
title: アーティクルの定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065769"
---
# <a name="define-an-article"></a>アーティクルの定義
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルを定義する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **アーティクルを定義するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   アーティクルの名前には % , * , [ , ] , | , : , " , ? を使用できません。 , ' , \ , / , \< , >. データベース内のオブジェクトにこれらの文字が使用されているときに、そのオブジェクトをレプリケートする場合、そのオブジェクト名とは異なる名前をアーティクルに指定する必要があります。  
  
##  <a name="security"></a><a name="Security"></a> セキュリティ  
 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&#xA0;Framework に用意されている](https://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] を使用します。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードにより、パブリケーションを作成し、アーティクルを定義します。 パブリケーションが作成されたら、[**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスでパブリケーションのプロパティを表示および変更します。 Oracle データベースからパブリケーションを作成する方法については、「[Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md)」(Oracle データベースからパブリケーションを作成する) をご覧ください。  
  
#### <a name="to-create-a-publication-and-define-articles"></a>パブリケーションを作成し、アーティクルを定義するには  
  
1.  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを右クリックします。  
  
3.  **[新しいパブリケーション]** をクリックします。  
  
4.  パブリケーションの新規作成ウィザードのページに従い、以下の操作を実行します。  
  
    -   サーバーでディストリビューションが構成されていない場合は、ディストリビューターを指定します。 ディストリビューションの構成の詳細については、「[Configure Publishing and Distribution](../configure-publishing-and-distribution.md)」(パブリッシュとディストリビューションの構成) をご覧ください。  
  
         **[ディストリビューター]** ページで、パブリッシャー サーバーが独自のディストリビューター (ローカル ディストリビューター) として機能するように指定した場合、このサーバーはディストリビューターとして構成されていないため、パブリケーションの新規作成ウィザードでサーバーを構成します。 **[スナップショット フォルダー]** ページで、ディストリビューターの既定のスナップショット フォルダーを指定します。 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 フォルダーの適切なセキュリティ保護の詳細については、「[Secure the Snapshot Folder](../security/secure-the-snapshot-folder.md)」(スナップショット フォルダーのセキュリティ保護) をご覧ください。  
  
         別のサーバーがディストリビューターとして機能するように指定する場合は、パブリッシャーからディストリビューターへの接続のため、 **[管理パスワード]** ページでパスワードを入力する必要があります。 このパスワードは、リモート ディストリビューターでパブリッシャーを有効にしたときに指定したパスワードと一致する必要があります。  
  
         詳しくは、「 [Configure Distribution](../configure-distribution.md)」を参照してください。  
  
    -   パブリケーション データベースを選択します。  
  
    -   パブリケーションの種類を選択します。 詳細については、「[Types of Replication](../types-of-replication.md)」(レプリケーションの種類) をご覧ください。  
  
    -   パブリッシュするデータおよびデータベース オブジェクトを指定します。必要に応じて、テーブル アーティクルから列をフィルター選択し、アーティクルのプロパティを設定します。  
  
    -   必要に応じて、テーブル アーティクルから行をフィルター選択します。 詳細については、「[パブリッシュされたデータのフィルター選択](filter-published-data.md)」を参照してください。  
  
    -   スナップショット エージェントのスケジュールを設定します。  
  
    -   以下のレプリケーション エージェントの実行および接続に使用される資格情報を指定します。  
  
         \-すべてのパブリケーション用のスナップショット エージェント。  
  
         \-すべてのトランザクション パブリケーション用のログ リーダー エージェント。  
  
         \-更新サブスクリプションを許可するトランザクション パブリケーションのキュー リーダー エージェント。  
  
         詳細については、「 [Replication Agent Security Model](../security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](../security/replication-security-best-practices.md)」を参照してください。  
  
    -   必要に応じて、パブリケーションのスクリプトを作成します。 詳しくは、「 [Scripting Replication](../scripting-replication.md)」をご覧ください。  
  
    -   パブリケーションの名前を指定します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリケーションが作成された後、プログラムでレプリケーション ストアド プロシージャを使用してアーティクルを作成できます。 アーティクルの作成に使用するストアド プロシージャは、定義するアーティクルのパブリケーションの種類によって決まります。 詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを定義するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前、**アーティクルのアーティクル名、 \@ ** ** \@ source_object**にパブリッシュされるデータベースオブジェクト、およびその他のオプションパラメーターを指定します。 **Dbo**以外の場合は、 ** \@ source_owner**を使用して、オブジェクトのスキーマ所有権を指定します。 アーティクルがログベースのテーブルアーティクルでない場合は、 ** \@ 種類**にアーティクルの種類を指定します。詳細については、「[レプリケーション Transact-sql プログラミング&#41;&#40;アーティクルの種類を指定](specify-article-types-replication-transact-sql-programming.md)する」を参照してください。  
  
2.  テーブル内の行を行方向にフィルター選択する場合、またはアーティクルを表示する場合は、 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を使用してフィルター句を定義します。 詳しくは、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
3.  テーブル内の列を列方向にフィルター選択する場合、またはアーティクルを表示する場合は、 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)を使用します。 詳しくは、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」をご覧ください。  
  
4.  アーティクルをフィルター選択する場合、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) を実行します。  
  
5.  パブリケーションに既存のサブスクリプションがあり、 [immediate_sync](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) 列の **sp_helppublication** が **0** を返す場合、 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を呼び出して既存の各サブスクリプションにアーティクルを追加する必要があります。  
  
6.  パブリケーションに既存のプル サブスクリプションがある場合、パブリッシャーで [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) を実行し、既存のプル サブスクリプションに対して新しいアーティクルのみを含む新しいスナップショットを作成します。  
  
    > [!NOTE]  
    >  スナップショットを使用して初期化しないサブスクリプションの場合、この処理は [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) によって実行されるため、 [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行する必要はありません。  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a>マージ パブリケーションのアーティクルを定義するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。 ** \@ パブリケーションの**名前、 ** \@ アーティクル**の名前、およびパブリッシュするオブジェクトを指定して、 ** \@ source_object**します。 テーブル行を行方向にフィルター選択するには、 ** \@ subset_filterclause**の値を指定します。 詳細については、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 」および「 [静的行フィルターの定義および変更](define-and-modify-a-static-row-filter.md)」を参照してください。 アーティクルがテーブルアーティクルでない場合は、[ ** \@ 種類**] にアーティクルの種類を指定します。 詳細については、「[Specify Article Types &#40;Replication Transact-SQL Programming&#41;](specify-article-types-replication-transact-sql-programming.md)」(アーティクルの種類の指定 (レプリケーション Transact-SQL プログラミング)) をご覧ください。  
  
2.  (省略可) パブリッシャー側のパブリケーション データベースに対して [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) を実行し、2 つのアーティクル間に結合フィルターを定義します。 詳しくは、「 [マージ アーティクル間の結合フィルターの定義および変更](define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
3.  (省略可) パブリッシャー側のパブリケーション データベースに対して [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) を実行し、テーブル列をフィルター選択します。 詳しくは、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」をご覧ください。  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、 `Product` テーブルに基づいてトランザクション パブリケーションにアーティクルを定義します。アーティクルは行方向および列方向にフィルター選択されます。  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 この例では、マージ パブリケーションのアーティクルを定義します。 `SalesOrderHeader` アーティクルは **SalesPersonID**に基づいて静的にフィルター選択され、 `SalesOrderDetail` アーティクルは `SalesOrderHeader`に基づいて結合フィルターが適用されます。  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってアーティクルを定義できます。 アーティクルの定義に使用する RMO クラスは、アーティクルを定義するパブリケーションの種類によって決まります。  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> 例 (RMO)  
 次の例では、行フィルターと列フィルターを含むアーティクルをトランザクション パブリケーションに追加します。  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 次の例では、マージ パブリケーションに 3 つのアーティクルを追加します。 このアーティクルには列フィルターがあり、2 つの結合フィルターを使用してパラメーター化された行フィルターを他のアーティクルに反映します。  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a>参照  
 [Create a Publication](create-a-publication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [既存のパブリケーションでのアーティクルの追加と削除](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [パブリッシュされたデータのフィルター処理](filter-published-data.md)   
 [データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
