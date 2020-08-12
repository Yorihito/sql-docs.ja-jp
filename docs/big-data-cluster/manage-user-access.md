---
title: Active Directory モードでビッグ データ クラスター アクセスを管理する
description: ビッグ データ クラスターへのアクセスを管理する
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 94719ef65023b1afd4edcf7770887323d0267127
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730621"
---
# <a name="manage-big-data-cluster-access-in-active-directory-mode"></a>Active Directory モードでビッグ データ クラスター アクセスを管理する

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

この記事では、clusterAdmins と clusterUsers の展開時に提供される Active Directory グループを更新する方法について説明します。

## <a name="two-overarching-roles-in-the-big-data-cluster"></a>ビッグ データ クラスターの 2 つの主要なロール

ビッグ データ クラスター内の承認に使用する 2 つの主要なロールの一部として、展開プロファイルのセキュリティ セクションで Active Directory グループを指定することができます。

* `clusterAdmins`:このパラメーターは、1 つの Active Directory グループを受け取ります。 このグループのメンバーには、クラスター全体の管理者アクセス許可が付与されます。 SQL Server に *sysadmin* アクセス許可、Hadoop 分散ファイル システム (HDFS) および Spark には *superuser* アクセス許可、コントローラーには *administrator* 権限が付与されます。

* `clusterUsers`:これらの Active Directory グループは、クラスターに管理者アクセス許可のない通常のユーザーです。 SQL Server マスター インスタンスにログインするアクセス許可が付与されますが、既定では、オブジェクトまたはデータに対するアクセス許可はありません。

展開後にビッグ データ クラスターに追加の Active Directory グループのアクセス許可を付与するには、展開時にユーザーとグループを登録済みのグループに追加する方法があります。 

ただし、管理者が Active Directory 内のグループ メンバーシップを常に変更できるとは限りません。 Active Directory 内のグループ メンバーシップを変更せずに追加の Active Directory グループのアクセス許可を付与するには、次のセクションの手順を完了します。

## <a name="grant-administrator-permissions-to-additional-active-directory-groups"></a>追加の Active Directory グループに管理者アクセス許可を付与する

>[!IMPORTANT]
>この手順を実行しても、追加の Active Directory グループに対して、ビッグ データ クラスター内の HDFS や Spark などの Hadoop コンポーネントへの管理者アクセス権は付与されません。 これらのコンポーネントでは、スーパーユーザー グループとして 1 つの Active Directory グループのみが許可されます。 この制限は、展開時に `clusterAdmins` で指定したグループは、この手順を実行した後もスーパーユーザー グループのままになることを意味します。

このセクションの手順を実行すると、コントローラーと SQL Server マスター インスタンスの両方への管理者アクセス権を付与できます。

### <a name="create-a-login-for-the-active-directory-user-or-group-in-the-sql-server-master-instance"></a>SQL Server マスター インスタンスで Active Directory ユーザーまたはグループのログインを作成する 

1. 好みの SQL クライアントを使用して、マスター SQL エンドポイントに接続します。 任意の管理者のログイン (たとえば、展開時に提供された `AZDATA_USERNAME`) を使用します。 または、セキュリティ構成で `clusterAdmins` として提供された Active Directory グループに属する任意の Active Directory アカウントを使用できます。

1. Active Directory ユーザーまたはグループのログインを作成するには、次の TSQL コマンドを実行します。

   ```sql
   CREATE LOGIN [<domain>\<principal>] FROM WINDOWS;
   ```

   SQL Server インスタンスで管理者アクセス許可を付与する場合は、次のアクセス許可も付与します。

   ```sql
   ALTER SERVER ROLE sysadmin ADD MEMBER [<domain>\<principal>];
   GO
   ```

### <a name="add-the-active-directory-user-or-group-to-the-roles-table-in-the-controller-database"></a>コントローラー データベースの roles テーブルに Active Directory ユーザーまたはグループを追加します。 

1. 次のコマンドを実行して、コントローラーの SQL server 資格情報を取得します。

   a. Kubernetes 管理者として次のコマンドを実行します。

   ```bash
   kubectl get secret controller-sa-secret -n <cluster name> -o yaml | grep password
   ```

   b. シークレットを Base64 でデコードします。

   ```bash
   echo <password from kubectl command>  | base64 --decode && echo
   ```

1. 別のコマンド ウィンドウで、コントローラー データベースのサーバー ポートを公開します。

   ```bash
   kubectl port-forward controldb-0 1433:1433 --address 0.0.0.0 -n <cluster name>
   ```

1. 前の接続を使用して、roles テーブルに行を挿入します。 大文字で「*REALM*」という値を入力します。

   管理者のアクセス許可を付与する場合は、 *\<role name>* に *bdcAdmin* ロールを使用します。 管理者以外のユーザーの場合は、*bdcUser* ロールを使用します。

   ```sql
   USE controller;
   GO

   INSERT INTO [controller].[auth].[roles] VALUES (N'<user or group name>@<REALM>', N'<role name>')
   GO
   ```

1. コントローラー エンドポイントにログインし、次のコマンドを実行して、追加したグループのメンバーにビッグ データ クラスター管理者アクセス許可が付与されていることを確認します。

   ```bash
   azdata bdc config show
   ```

1. 管理者以外のユーザーの場合、`azdata login` を使用して SQL マスター インスタンスまたはコントローラーへの認証を受けることで、アクセスを確認できます。

## <a name="next-steps"></a>次のステップ

- [SQL Server 2019 ビッグ データ クラスターのセキュリティの概念](concept-security.md)
