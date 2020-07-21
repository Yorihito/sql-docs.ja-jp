---
title: Active Directory モードでの展開
titleSuffix: SQL Server Big Data Cluster
description: Active Directory ドメインで SQL Server ビッグ データ クラスターをアップグレードする方法について説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 02/28/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2bbacb2bdeeb409f08e6e68438535bc0d6671b01
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79487620"
---
# <a name="deploy-big-data-clusters-2019-in-active-directory-mode"></a>Active Directory モードで [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] を展開する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このドキュメントでは、認証に既存の AD ドメインを使用する Active Directory 認証モードで SQL Server 2019 ビッグ データ クラスター (BDC) を展開する方法について説明します。

## <a name="background"></a>バックグラウンド

Active Directory (AD) 認証を有効にするために、BDC では、クラスター内のさまざまなサービスで必要となるユーザー、グループ、コンピューター アカウント、サービス プリンシパル名 (SPN) が自動的に作成されます。 このようなアカウントを一部含め、スコーピングを許可するため、BDC 関連のあらゆる AD オブジェクトが作成される展開中に組織単位 (OU) を指名します。 クラスター展開前にこの OU を作成します。

Active Directory で必須のオブジェクトをすべて自動作成するには、展開中、BDC に AD アカウントが必要になります。 このアカウントには、指定の OU 内でユーザー、グループ、コンピューター アカウントを作成する権限を与える必要があります。

次の手順では、Active Directory ドメイン コントローラーを既に用意していることを前提としています。 ドメイン コントローラーがない場合、[こちら](https://social.technet.microsoft.com/wiki/contents/articles/37528.create-and-configure-active-directory-domain-controller-in-azure-windows-server.aspx)のガイドに含まれる手順が参考になります。

## <a name="create-ad-objects"></a>AD オブジェクトの作成

AD 統合で BDC を展開する前に次の操作を行います。

1. すべての BDC AD オブジェクトを格納する組織単位 (OU) を作成します。 展開時、既存の OU を指名することもできます。
1. BDC の AD アカウントを作成するか、既存のアカウントを使用し、この BDC AD アカウントに正しい権限を付与します。

### <a name="create-a-user-in-ad-for-bdc-domain-service-account"></a>BDC ドメイン サービス アカウントの AD でユーザーを作成する

ビッグ データ クラスターには、特定のアクセス許可を持つアカウントが必要です。 続行する前に、既存の AD アカウントを持っていることを確認するか、新しいアカウントを作成します。このアカウントは、ビッグ データ クラスターで必要なオブジェクトを設定するために使用できます。

AD で新しいユーザーを作成するには、ドメインまたは OU を右クリックし、 **[新規]** 、 **[ユーザー]** の順に選択します。

![image12](./media/deploy-active-directory/image12.png)

このユーザーは、この記事で *BDC ドメイン サービス アカウント*と呼びます。

### <a name="creating-an-ou"></a>OU の作成

ドメイン コントローラーで、 **[Active Directory ユーザーとコンピューター]** を開きます。 左側のパネルで、OU を作成するディレクトリを右クリックし、[新規] -\> **[組織単位]** の順に選択します。次に、ウィザードの指示に従って OU を作成します。 または、PowerShell で OU を作成できます。

```powershell
New-ADOrganizationalUnit -Name "<name>" -Path "<Distinguished name of the directory you wish to create the OU in>"
```

この記事の例では、OU に `bdc` という名前を付けます。

![image13](./media/deploy-active-directory/image13.png)

![image14](./media/deploy-active-directory/image14.png)

### <a name="setting-permissions-the-bdc-ad-account"></a>BDC AD アカウントのアクセス許可を設定する

新しい AD ユーザーを作成したか、既存の AD ユーザーを使用しているかに関係なく、ユーザーには特定のアクセス許可を与える必要があります。 このアカウントは、クラスターを AD に参加させるとき、BDC コントローラーによって使用されるユーザー アカウントです。

BDC ドメイン サービス アカウント (DSA) は、OU でユーザー、グループ、コンピューター アカウントを作成できる必要があります。 次の手順では、BDC ドメイン サービス アカウントに `bdcDSA` という名前を付けています。 このアカウントには任意の名前を選択できます。

1. ドメイン コントローラーで、 **[Active Directory ユーザーとコンピューター]** を開きます。

1. 左側のパネルでドメインに移動し、`bdc` で使用される OU に移動します。

1. OU を右クリックし、 **[プロパティ]** を選択します。

1. [セキュリティ] タブに移動します (OU を右クリックし、 **[表示]** を選択し、 **[高度な機能]** が選択されていることを確認してください)。

    ![image15](./media/deploy-active-directory/image15.png)

1. **[追加]** をクリックし、**bdcDSA** ユーザーを追加します。

    ![image16](./media/deploy-active-directory/image16.png)

    ![image17](./media/deploy-active-directory/image17.png)

1. **bdcDSA** ユーザーを選択し、アクセス許可をすべて消去し、 **[詳細]** をクリックします。

1. **[追加]** をクリックします。

    ![image18](./media/deploy-active-directory/image18.png)

    - **[プリンシパルの選択]** をクリックし、**bdcDSA** を挿入し、[OK] をクリックします。

    - **[種類]** を **[許可]** に設定します。

    - **[適用先]** を **[このオブジェクトとすべての子オブジェクト]** に設定します。

        ![image19](./media/deploy-active-directory/image19.png)

    - 一番下までスクロールし、 **[すべて消去]** をクリックします。

    - スクロールで一番上まで戻り、次を選択します。
       - **すべてのプロパティの読み取り**
       - **すべてのプロパティの書き込み**
       - **コンピューター オブジェクトの作成**
       - **コンピューター オブジェクトの削除**
       - **グループ オブジェクトの作成**
       - **グループ オブジェクトの削除**
       - **ユーザー オブジェクトの作成**
       - **ユーザー オブジェクトの削除**

    - **[OK]**

- **[追加]** をクリックします。

    - **[プリンシパルの選択]** をクリックし、**bdcDSA** を挿入し、[OK] をクリックします。

    - **[種類]** を **[許可]** に設定します。

    - **[適用先]** を **[Descendant Computer objects]\(子コンピューター オブジェクト\)** に設定します。

    - 一番下までスクロールし、 **[すべて消去]** をクリックします。

    - スクロールで一番上まで戻り、 **[パスワードのリセット]** を選択します。

    - **[OK]**

- **[追加]** をクリックします。

    - **[プリンシパルの選択]** をクリックし、**bdcDSA** を挿入し、[OK] をクリックします。

    - **[種類]** を **[許可]** に設定します。

    - **[適用先]** を **[Descendant User objects]\(子ユーザー オブジェクト\)** に設定します。

    - 一番下までスクロールし、 **[すべて消去]** をクリックします。

    - スクロールで一番上まで戻り、 **[パスワードのリセット]** を選択します。

    - **[OK]**

- **[OK]** をさらに 2 回クリックしてダイアログ ボックスを開きます。

## <a name="prepare-deployment"></a>展開の準備

AD 統合で BDC を展開するためには、AD で BDC 関連のオブジェクトを作成するために必要な情報をいくつか追加します。

`kubeadm-prod` プロファイルを利用することで、AD 統合に必要なセキュリティ関連の情報とエンドポイント関連の情報のプレースホルダーが自動的に作成されます。

さらに、AD で必要なオブジェクトを作成するために [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] で使用される資格情報を提供する必要があります。 これらの資格情報は環境変数として提供されます。

## <a name="set-security-environment-variables"></a>セキュリティ環境変数の設定

次の環境変数からは、BDC ドメイン サービス アカウントの資格情報が与えられます。この情報が AD 統合の設定に使用されます。 このアカウントはまた、この先、BDC 関連の AD オブジェクトを維持する目的で BDC によって使用されます。

```bash
export DOMAIN_SERVICE_ACCOUNT_USERNAME=<AD principal account name>
export DOMAIN_SERVICE_ACCOUNT_PASSWORD=<AD principal password>
```

## <a name="provide-security-and-endpoint-parameters"></a>セキュリティとエンドポイントのパラメーターを指定する

資格情報の環境変数に加えて、AD 統合が機能するためのセキュリティとエンドポイントの情報も提供する必要があります。 必要なパラメーターは、自動的に `kubeadm-prod` [展開プロファイル](deployment-guidance.md#configfile)に含まれます。

AD 統合には次のパラメーターが必要です: この記事の後半に出てくる `config replace` コマンドを使用し、`control.json` ファイルと `bdc.json` ファイルにこれらのパラメーターを追加します。 下の例ではすべて、サンプル ドメイン `contoso.local` が使用されています。

- `security.activeDirectory.ouDistinguishedName`: クラスターにより作成されたあらゆる AD アカウントが追加される組織単位 (OU) の識別名。 ドメインの名前が `contoso.local` の場合、OU の識別名は `OU=BDC,DC=contoso,DC=local` です。

- `security.activeDirectory.dnsIpAddresses`: ドメインの DNS サーバーの IP アドレスの一覧が含まれます。 

- `security.activeDirectory.domainControllerFullyQualifiedDns`:ドメイン コントローラーの FQDN の一覧。 FQDN には、ドメイン コントローラーのコンピューター名またはホスト名が含まれています。 複数のドメイン コントローラーがある場合、ここで一覧を指定できます。 例: `HOSTNAME.CONTOSO.LOCAL`

- `security.activeDirectory.realm` **省略可能なパラメーター**: ほとんどの場合、領域はドメイン名と同じです。 同じでない場合、このパラメーターを使用し、領域の名前を定義します (例: `CONTOSO.LOCAL`)。

- `security.activeDirectory.domainDnsName`:ドメインの名前 (例: `contoso.local`)。

- `security.activeDirectory.clusterAdmins`:このパラメーターは、1 つの AD グループを受け取ります。 AD グループのスコープは、ユニバーサルまたはドメイン グローバルである必要があります。 このグループのメンバーには、クラスターの管理者権限が与えられます。 これは、SQL Server で `sysadmin` 権限が、HDFS でスーパーユーザー権限が、コントローラーで管理者権限が与えられることを意味します。 

  >[!IMPORTANT]
  >展開を開始する前に、このグループを AD 内に作成します。 この AD グループのスコープがドメイン ローカルの場合、展開は失敗します。

- `security.activeDirectory.clusterUsers`:ビッグ データ クラスター内で通常のユーザー (管理者権限なし) となる AD グループの一覧。 この一覧には、ユニバーサル グループまたはドメイン グローバル グループのいずれかのスコープを持つ AD グループを含めることができます。 ドメイン ローカル グループを含めることはできません。

  >[!IMPORTANT]
  >展開を開始する前に、これらのグループを AD 内に作成します。 これらの AD グループのいずれかのスコープがドメイン ローカルの場合、展開は失敗します。

- `security.activeDirectory.appOwners` **省略可能なパラメーター**: あらゆるアプリケーションを作成、削除、実行する権限が与えられる AD グループの一覧。 この一覧には、ユニバーサル グループまたはドメイン グローバル グループのいずれかのスコープを持つ AD グループを含めることができます。 ドメイン ローカル グループを含めることはできません。

  >[!IMPORTANT]
  >展開を開始する前に、これらのグループを AD 内に作成します。 これらの AD グループのいずれかのスコープがドメイン ローカルの場合、展開は失敗します。

- `security.activeDirectory.appReaders` **省略可能なパラメーター**: あらゆるアプリケーションを実行する権限を持つ AD グループの一覧。 この一覧には、ユニバーサル グループまたはドメイン グローバル グループのいずれかのスコープを持つ AD グループを含めることができます。 ドメイン ローカル グループを含めることはできません。

  >[!IMPORTANT]
  >展開を開始する前に、これらのグループを AD 内に作成します。 これらの AD グループのいずれかのスコープがドメイン ローカルの場合、展開は失敗します。

[AD グループのスコープを確認](https://docs.microsoft.com/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps)し、DomainLocal であるかどうかを確認します。

展開構成ファイルをまだ初期化していない場合、このコマンドを実行して構成のコピーを取得できます。

```bash
azdata bdc config init --source kubeadm-prod  --target custom-prod-kubeadm
```

`control.json` ファイルで上記のパラメーターを設定するには、次の `azdata` コマンドを使用します。 これらのコマンドによって展開前に構成が置換され、独自の値が提供されます。

 > [!IMPORTANT]
 > SQL Server 2019 CU2 リリースでは、展開プロファイルのセキュリティ構成セクションの構造が多少変更され、Active Directory 関連の設定はすべて、*control.json* ファイル内の *security* の下にある json ツリー内の新しい *activeDirectory* 内にあります。

次の例は、SQL Server 2019 CU2 の使用に基づいています。 この例は、展開構成内の AD 関連のパラメーター値を置き換える方法を示しています。下のドメインの詳細はサンプルの値です。

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

同様に、SQL Server 2019 CU2 以前のリリースでは、次のことを実行できます。

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

上記の情報に加え、さまざまなクラスター エンドポイントの DNS 名を指定する必要もあります。 指定した DNS 名を使用する DNS エントリは、展開時に DNS サーバーで自動的に作成されます。 これらの名前は、さまざまなクラスター エンドポイントに接続するときに使用します。 たとえば、SQL マスター インスタンスの DNS 名が `mastersql` の場合、`mastersql.contoso.local,31433` を使用し、ツールからマスター インスタンスに接続します。

> [!NOTE]
> 下記で定義する名前に対して DNS サーバーで DNS エントリを必ず作成してください。 `kubeadm` の展開では、たとえば、DNS エントリを作成するときに Kubernetes マスター ノードの IP アドレスを使用できます。

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[1].dnsName=<monitoring services DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=<SQL Master Primary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=<SQL Master Secondary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=<Gateway (Knox) DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=<app proxy DNS name>.<Domain name. e.g. contoso.local>"
```

AD 統合を利用し、単一ノード Kubernetes クラスター (kubeadm) で SQL Server ビッグ データ クラスターを展開するサンプル スクリプトは[こちら](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm-ad)にあります。

これで、Active Directory 統合を使用し、BDC の展開に必要なパラメーターをすべて設定できたはずです。

`azdata` コマンドと kubeadm-prod デプロイ プロファイルを使用して、Active Directory と統合された BDC クラスターをデプロイできるようになりました。 [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] をデプロイする方法の完全なドキュメントについては、「[Kubernetes 上に SQL Server ビッグ データ クラスターを展開する方法](deployment-guidance.md)」を参照してください。

## <a name="verify-reverse-dns-entry-for-domain-controller"></a>ドメイン コントローラーの逆引き DNS エントリを確認する

ドメイン コントローラー自体の逆引き DNS エントリ (PTR レコード) が DNS サーバーに登録されていることを確認します。 これは、ドメイン コントローラーでドメイン名の `nslookup` を実行し、ドメイン名がドメイン コントローラー IP アドレスで解決されるかを調べることで確認できます。

## <a name="connect-to-cluster-endpoints-in-ad-mode"></a>AD モードでクラスター エンドポイントに接続する

AD Auth を使用して SQL Server マスター インスタンスにログインします。

SQL Server インスタンスへの AD 接続を確認するには、`sqlcmd` を使用して SQL マスター インスタンスに接続します。 展開時、指定されたグループに対してログインが自動的に作成されます (`clusterUsers` と `clusterAdmins`)。

Linux を使用している場合、最初に AD ユーザーとして `kinit` を実行し、次に `sqlcmd` を実行します。 Windows を使用している場合、**ドメインに参加しているクライアント コンピューター**から目的のユーザーとしてログインします。

### <a name="connect-to-master-instance-from-linuxmac"></a>Linux/Mac からマスター インスタンスに接続する

```bash
kinit <username>@<domain name>
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="connect-to-master-instance-from-windows"></a>Windows からマスター インスタンスに接続する

```cmd
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="log-in-to-sql-server-master-instance-using-azure-data-studio-or-ssms"></a>Azure Data Studio または SSMS を使用し、SQL Server マスター インスタンスにログインする

ドメインに参加しているクライアントから、SSMS または Azure Data Studio を開き、マスター インスタンスに接続できます。 これは、AD 認証を使用して SQL Server インスタンスに接続する場合と同じです。

SSMS から:

![image23](./media/deploy-active-directory/image23.png)

Azure Data Studio から:

![image24](./media/deploy-active-directory/image24.png)}

### <a name="log-in-to-controller-with-ad-authentication"></a>AD 認証を使用してコントローラーにログインする

#### <a name="connect-to-controller-with-ad-authentication-from-linuxmac"></a>Linux/Mac から AD 認証を使用してコントローラーに接続する

`azdata` と AD 認証を使用し、コントローラー エンドポイントに接続できます。

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

#### <a name="connect-to-controller-with-ad-authentication-from-windows"></a>Windows から AD 認証を使用してコントローラーに接続する

```cmd
azdata login -e https://<controller DNS name>:30080 --auth ad
```

### <a name="use-ad-authentication-to-knox-gateway-webhdfs"></a>Knox ゲートウェイ (webHDFS) に AD 認証を使用する

Knox ゲートウェイ エンドポイント経由で curl を使用して HDFS コマンドを発行することもできます。 これには Knox の AD 認証が必要です。 次の curl コマンドでは、Knox ゲートウェイを介して webHDFS REST 呼び出しが発行され、`products` という名前のディレクトリが作成されます。

```bash
curl -k -v --negotiate -u : https://<Gateway DNS name>:30443/gateway/default/webhdfs/v1/products?op=MKDIRS -X PUT
```

## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

**このリリースで注意すべき制限事項:**

- 現在のところ、ログ検索ダッシュボードとメトリクス ダッシュボードは AD 認証に対応していません。 このエンドポイントの AD サポートは今後のリリースで予定されています。 展開時に設定される基本ユーザー名とパスワードは、これらのダッシュボードに対する認証に使用することができます。 他のすべてのクラスター エンドポイントは、AD 認証に対応しています。

- セキュア AD モードは現在のところ、`kubeadm` 展開環境でのみ動作し、AKS では動作しません。 `kubeadm-prod` 展開プロファイルには既定で、セキュリティ セクションが含まれています。

- 現時点では、ドメイン (Active Directory) につき BDC が 1 つだけ許可されています。 今後のリリースでは、ドメインあたり複数の BDC を有効にできるようになる予定です。

- セキュリティ構成で指定されているどの AD グループも、DomainLocal にスコープ指定できません。 AD グループのスコープは、[この手順](https://docs.microsoft.com/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps)に従って確認できます。

- BDC へのログインに使用できる AD アカウントは、BDC 用に構成されたのと同じドメインから許可されています。他の信頼される側のドメインからのログインは、将来のリリースで有効になる予定です。
