---
title: CDC 用の SQL Server の準備 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d1c597b03375fab0846130d7dc42c91faa5f8bd
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85435669"
---
# <a name="prepare-sql-server-for-cdc"></a>CDC 用の SQL Server の準備
  Oracle CDC サービスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのターゲット インスタンスに MSXDBCDC データベースが含まれている必要があります。 このデータベースを作成するには、CDC Service 構成コンソールの "SQL Server の準備" アクションを使用します。 これによって作成される特別なスクリプトを実行すると、このデータベースに必要なテーブル、ストアド プロシージャ、およびその他のアーティファクトが作成されます。 このタスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各ターゲット インスタンスに対して一度だけ実行します。  
  
 MSXDBCDC データベースの詳細については、「MSXDBCDC データベース」を参照してください。  
  
 CDC Service 構成コンソールで **[SQLServer の準備]** をクリックします。 このオプションを利用できない場合は、コンソールの左ペインで **[ローカルの CDC Service]** が選択されていることを確認してください。  
  
## <a name="options"></a>Options  
  
### <a name="server-name"></a>サーバー名  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。  
  
### <a name="authentication"></a>認証  
 次のいずれかを選択してください。  
  
-   **[Windows 認証]**  
  
-   **[SQL Server 認証]** : このオプションを選択する場合、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。  
  
 Oracle CDC 用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備するには、ログインが MSXDBCDC データベースに対する書き込み権限を持っている必要があります。 `sysasmin` ロールのメンバーなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力します。  
  
### <a name="options"></a>Options  
 矢印をクリックして、構成するオプションを表示します。 これらのオプションを既定値のままにすることもできます。 使用可能なオプションは次のとおりです。  
  
-   **[接続タイムアウト]** : CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。  
  
-   **[実行タイムアウト]** : Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。  
  
-   **[暗号化接続]** : Oracle CDC Service とターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間の暗号化された接続を使用した通信に対しては、 **[暗号化接続]** を選択します。  
  
-   **[詳細設定]** :必要に応じて、追加の接続プロパティを入力します。  
  
### <a name="view-script"></a>[スクリプトの表示]  
 セットアップ スクリプトの読み取り専用バージョンを表示するには、 **[スクリプトの表示]** をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム管理者は、必要に応じて、SQL Server 管理コンソールにこのスクリプトをコピーして編集することができます。 SQL Server スクリプトの準備については、「 [Oracle CDC 表示スクリプト用の SQL Server の準備](prepare-sql-server-for-oracle-cdc-view-script.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC Service の操作方法](work-with-cdc-services.md)   
 [CDC 用に SQL Server を準備する方法](prepare-sql-server-for-cdc.md)  
  
  
