---
title: SharePoint 用 Reporting Services アドインのインストールまたはアンインストール (SharePoint 2010 および SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 63f45fa174296e4ce79985236da2d97d3f11e937
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289440"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a>SharePoint 用 Reporting Services アドインのインストールまたはアンインストール (SharePoint 2010 および SharePoint 2013)
  Sharepoint サーバー上の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 製品用のインストールパッケージ (rssharepoint .msi) を実行して、sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]配置内の機能を有効にします。 提供される機能には、Power View、レポート ビューアー Web パーツ、URL プロキシ エンドポイント、コンテンツの種類、アプリケーション ページなどがあります。これにより、レポート、レポート モデル、データ ソース、およびその他のレポート サーバー コンテンツを SharePoint サイト上で作成、表示、管理できます。 SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインは、SharePoint モードで実行されるレポート サーバーに必要なコンポーネントです。 アドインは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードからインストールするか、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 機能パックから rsSharePoint.msi をダウンロードしてインストールすることができます。 アドインのバージョンの一覧およびダウンロード ページについては、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010|

 **このトピックの内容:**

-   [必要条件](#bkmk_prereq)

-   [アドインがインストールする内容](#bkmk_whatinstalled)

-   [インストール方法の概要](#bkmk_3ways_to_install)

-   [インストールファイル rsSharePoint .msi を使用してアドインをインストールする](#bkmk_install_rssharepoint)

    -   [ファイルのみのインストール](#bkmk_files_only_installation)

-   [Reporting Services アドインを削除する方法](#bkmk_remove_addin)

-   [コマンド ラインから rssharepoint.msi を修復する方法](#bkmk_repair)

-   [セットアップ ログ ファイル](#bkmk_logfiles)

-   [アップグレード](#bkmk_upgrade)

-   [rsCustomAction.exe](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> 前提条件
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのインストールは、レポート サーバーと SharePoint 製品のインスタンスを統合するために必要ないくつかの手順の 1 つです。 SharePoint モードの使用のすべての前提条件の詳細については、「 [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md)」を参照してください。 のインストールと構成[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の詳細については、「 [sharepoint 2013 用 Reporting Services Sharepoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)」を参照してください。

-   複数の Web フロントエンド アプリケーションがある SharePoint ファームに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する場合は、Web サーバー フロントエンドがあるファームの各コンピューターにアドインをインストールします。 この作業は、レポート サーバー コンテンツのアクセスに使用する Web フロントエンドに対してのみ行ってください。

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールするには、コンピューターの管理者である必要があります。 たとえば、コマンド プロンプトで rsSharePoint.msi を実行する場合は、 **[管理者として実行]** オプションを使用して、管理者特権でコマンド プロンプトを開く必要があります。

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールするには、SharePoint ファーム管理者グループのメンバーである必要があります。

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 統合機能をアクティブ化するには、サイト コレクションの管理者である必要があります。

-   アドインを使用した配置例の図については、「 [SharePoint の SQL SERVER BI 機能の配置トポロジ](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)」を参照してください。

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a>アドインはどのようにインストールされますか。
 アドインのセットアップ プロセスは、2 つのフェーズで構成されます。標準インストールが完了すると、どちらのフェーズも自動的に完了します。

-   最初のフェーズでは、正しいフォルダーにファイルをインストールします。 それらのフォルダーは、SharePoint 配置では標準です。 インストールされるファイルの 1 つに rsCustomAction.exe ファイルがあります。

-   インストールの 2 つ目の部分では、一連のカスタム アクションを実行して、SharePoint に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ファイルを登録します。 カスタム アクションは、rsCustomAction.exe から実行します。 2 つのフェーズで構成される完全なインストールが終了すると、exe ファイルは削除されます。 **[ファイルのみ]** のインストールを実行すると、インストールの終わりに rsCustomAction.exe は実行されず、ドライブに残ります。

## <a name="the-reporting-services-installation-order"></a>Reporting Services のインストールの順序
 アドインは、SharePoint をインストールする前でも後でもインストールできます。 アドインは、SharePoint の配置前の標準に準拠し、SharePoint のインストールで使用された場所にファイルをインストールします。

> [!NOTE]
>  SharePoint 製品より前にアドインをインストールする利点は、新しいサーバーをファームに追加すると、Reporting Services アドインが SharePoint ファームによって構成およびアクティブ化されることです。

 **SharePoint 2010**

-   SharePoint 2010 製品準備ツールにより、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインがインストールされます。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]には、の機能に[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]必要な新しいバージョンのアドインが含まれています。

     SharePoint 製品準備ツールを実行する場合でも、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。

-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールした場合は、SharePoint 製品準備ツールを実行すると、新しいバージョンが検知されたために準備ツールによってアドインの旧バージョンがインストールされなかったことを示す次のダイアログが表示されます。 これは想定されている動作です。

     ![SSRS アドインが既にインストールされています。](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS アドインが既にインストールされています。")

 **SharePoint 2013**

 SharePoint 20103 製品準備ツールでは、SharePoint 製品[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]用アドインはインストール**されません**。

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a> インストール方法の概要
 SharePoint [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]製品用アドインは、次の2つの方法のいずれかを使用してインストールできます。

-   **インストールウィザード:** ![で](../../../2014/reporting-services/media/rs-fyinote.png "注意") [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]新しく導入されたアドインは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールウィザードでインストールできます。 ウィザードの **[機能の選択]** ページで、 **[SharePoint 製品用 Reporting Services アドイン]** を選択します。

-   **rsSharepoint.msi:** インストール メディアまたはダウンロードからアドインを直接インストールする。 rsSharepoint.msi は、グラフィカル ユーザー インターフェイスもコマンド ライン インストールもサポートしています。 .msi を管理者特権を使用して実行する必要があるため、まず高度な権限でコマンド プロンプトを開いてから、コマンド ラインから rsSharepoint.msi を実行します。 アドインのダウンロードの詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。

    > [!NOTE]
    >  サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。 インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a> rsSharePoint.msi インストール ファイルを使用したアドインのインストール
 このセクションは、.msi インストール ウィザードの実行またはコマンド ライン インストールにより、rssharepoint.msi を直接インストールすることに関連しています。 SQL Server インストール ウィザードを使用してアドインをインストールする場合は、次の手順を実行する必要はありません。

 次のコマンドを実行すると、コマンド ライン スイッチの全リストが表示されます。

```
Rssharepoint.msi /?
```

1.  アドインのセットアッププログラム (`rsSharepoint.msi`) をダウンロードします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのダウンロードの詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。

2.  管理者は、`rsSharepoint.msi` を実行して、インストール ウィザードを実行します。 ウィザードに、"ようこそ" ページ、ソフトウェア ライセンス条項、および登録情報ページが表示されます。 セットアップ時に、次のパスにフォルダーが作成され、そのフォルダーにファイルがコピーされます。

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     or

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  SharePoint サーバーの全体管理で、レポート サーバーの設定と機能のアクティブ化を構成します。 . Sharepoint モードのインストールと構成[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の詳細については、「sharepoint [2010 用 Reporting Services Sharepoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」を参照してください。

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a>ファイルのみのインストール
 インストールのカスタム アクション フェーズをスキップしてファイルをインストールするには、SKIPCA オプションを指定してコマンド ラインから rssharepoint.msi を実行します。

1.  **管理者権限を使用して**コマンド プロンプトを開きます。

2.  次のコマンドを実行します。

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 インストールのユーザー インターフェイスが開き、正常に実行され、`rsCustomAction.exe` ファイルがインストールされます。 ただし、.exe はインストールの終了時には実行されず、インストールの終了後、`rsCustomAction.exe` はコンピューター上に残ります。

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a>2 ステップのインストールを使用したインストールの問題のトラブルシューティングまたはコンテンツの種類のインストール
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンテンツの種類のインストール中にエラーが発生するか、コンテンツの種類がドキュメント ライブラリの設定に表示されない場合は、コマンド ラインから Setup を 2 ステップ プロセスとして実行します。

1.  **管理者権限で** コマンド プロンプトを開き、前のセクションの説明に従い、ファイルのみのインストールを実行します。

2.  カスタム アクションの実行可能ファイルを実行します。

    1.  `rsCustomAction.exe` ファイルのあるフォルダーに移動します。 このファイルは、アドインのファイルのみのインストールを実行することで、コンピューターにコピーされます。 `rsCustomAction.exe`は **% Temp%** ディレクトリにあります。 ファイルに移動するには、コマンド プロンプトから次のように入力します。

         **CD %temp%**。

         ファイルを **\Users\\<ユーザー名\>\AppData\Local\Temp** に配置する必要があります。

    2.  次のコマンドを入力します。 この構成手順は、完了まで数分かかります。 この処理中に W3SVC サービスが再起動されます。 プログラムでファイルがコピーされ、コンポーネントが登録され、SharePoint 製品構成ウィザードが実行されると共に、状態メッセージが表示されます。

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  変更が有効になるまでの時間はサーバー環境によって異なる場合があります。 **iisreset** 実行して、更新にかかる時間を短縮することもできます。

### <a name="quiet-installation-for-scripting"></a>スクリプト作成のためのサイレント インストール
 **/Q**または **/quiet**スイッチを使用して、ダイアログや警告が表示されない "quiet" インストールを行うことができます。 サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。

> [!NOTE]
>  サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。 インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。

 サイレント インストールを行うには、次の手順を実行します。

1.  **管理者権限を使用して**コマンド プロンプトを開きます。

2.  次のコマンドを実行します。

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a>Reporting Services アドインを削除する方法
 SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコントロール パネルまたはコマンド ラインからアンインストールできます。

1.  コントロール パネルを使用すると、現在のコンピューター上のファイルが完全にアンインストールされます。 **さらに** 、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のオブジェクトと機能が SharePoint ファームから削除されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のオブジェクトと機能が削除されると、レポートの確認と更新ができなくなります。

2.  コマンド ラインでアドインをアンインストールする場合は、LocalOnly パラメーターを使用して、ローカル コンピューターからアドイン ファイルのみを削除できます。ファーム内にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のオブジェクトと機能は変更されません。

 アドインをアンインストールすると、レポート サーバーでレポートの処理に使用されているサーバー統合機能が削除されます。 SharePoint サーバーの全体管理ページおよびその他のカスタム [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ページから、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページも削除されます。 また、影響を受ける SharePoint サイトで、今後使用しないレポートとその他のレポート サーバー アイテムをすべて削除することもできます。 これらは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを削除すると実行できなくなります。

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをアンインストールするには、[!INCLUDE[SPF2010](../../includes/spf2010-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] がインストールされている必要があります。 SharePoint 2010 を先にアンインストールした場合は、それを再インストールしないと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをアンインストールできません。

 アドインをアンインストールする手順は、スタンドアロンのサーバーの場合もサーバー ファームの場合も同じです。 セットアップにより、インストール時に追加されたプログラム ファイルと構成設定が削除されます。

 アドインをアンインストールしても次のものは削除されません。

-   SharePoint の構成データベースとコンテンツ データベースへのアクセスに使用される、レポート サーバー サービス アカウント用に作成されたログイン。 レポートサーバーサービスアカウントのすべてのログインは、SharePoint データベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]ホストに使用するインスタンスから削除する必要があります。

-   レポート ユーザー用に作成した権限またはグループ。 レポート サーバーの機能へのアクセスを許可するためにカスタム権限レベルまたは SharePoint グループを作成した場合は、不要になった権限を取り消す必要があります。

-   SharePoint ライブラリにアップロードしたデータ ファイル。レポート定義 (.rdl)、共有データ ソース (.rsds)、パブリッシュ済みレポート アイテム (.rsc) などのファイルは 削除されませんが、実行されなくなります。 これらのファイルは手動で削除する必要があります。

-   セットアップによって、レポート サーバー データベースが削除されたり、統合操作に使用されていたレポート サーバー インスタンスが変更されることはありません。

### <a name="to-uninstall-from-windows-control-panel"></a>Windows のコントロール パネルからアンインストールを行うには
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコントロール パネルからウィザードを起動してアドインを削除するには、次の手順を実行します。

1.  コントロール パネルの **[プログラム]** で、 **[プログラムのアンインストール]** をクリックします。

2.  **[SharePoint 用 Microsoft SQL Server RS アドイン]** を選択します。 コマンド プロンプトから、スイッチを指定せずに **rssharepoint.msi** を実行してアンインストール ウィザードを起動することもできます。

3.  **[除去]** をクリックします。

### <a name="uninstall-from-the-command-line"></a>コマンドラインからアンインストールする
 アドインをコマンド ラインからアンインストールするには、次の手順を実行します。

1.  **管理者権限を使用して**コマンド プロンプトを開きます。

2.  次のコマンドを実行します。

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  確認メッセージ ボックスが表示されます。 **[はい]** をクリックします。

### <a name="uninstall-the-add-in-from-the-local-server-only"></a>ローカル サーバーのみからのアドインのアンインストール
 前に説明したアドインのアンインストール方法では、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能とオブジェクトがファームから削除されます。 マルチサーバー ファームにおいて、ローカル コンピューターからのみアドインをアンインストールして、SharePoint ファームは稼働させておく場合は、次の手順を実行します。

1.  **管理者権限を使用して**コマンド プロンプトを開きます。

2.  次のコマンドを実行します。

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 これにより、SharePoint から [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの登録が解除され、ファイルが削除されます。ただし対象は、ローカル コンピューターのみです。

 SharePoint から [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能の登録を解除するが、後で使用するためにファイルをディスクに残しておくには、次の手順を実行します。

1.  **管理者権限を使用して**コマンド プロンプトを開きます。

2.  次のコマンドを実行します。

    ```cmd
    rsCustomAction.exe /p
    ```

 上記の手順は、SkipCA=1 で .msi がインストールされていること、および rscusstomaction.exe が使用可能であることを前提としています。 詳細については、ファイルのみのインストールを説明したセクションを参照してください。

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a>コマンドラインから rssharepoint .msi を修復する方法
 コマンド ラインを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを修復またはアンインストールするには、次の手順を実行します。

1.  **管理者権限を使用して**コマンド プロンプトを開きます。

2.  次のコマンドを実行します。

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a>セットアップログファイル
 セットアップの実行中は、 **アドインをインストールしたユーザーの** %temp% [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] フォルダー内のログ ファイルに情報が記録されます。 たとえば、 **c:\Users\\<username\>\AppData\Local\Temp**のようになります。ファイル名は、 **RS_SP_0**.log などの**RS_SP_\<>** です。 ログ内では、エラーは "SSRSCustomActionError" という文字列から始まります。

> [!NOTE]
>  AppData は Windows オペレーティング システム内の隠れたフォルダーです。 隠れたファイルとフォルダーを表示するには、Windows エクスプローラーのフォルダー設定を変更する必要がある場合があります。

#### <a name="view-a-log-file-with-windows-notepad"></a>Windows メモ帳でのログ ファイルの表示

1.  次のコマンドは、コマンド プロンプトのパスを変更し、rs ログ ファイルを一覧表示し、Windows メモ帳でそれらのファイルの 1 つを表示します。

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a>PowerShell でのログ ファイルの表示

1.  SharePoint 管理シェルから次のコマンドを入力すると、フィルター選択された "ssrscustomactionerror" を含む行の一覧がファイルから返されます。

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  出力は次のようになります。

     `2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a>増設
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインの既存のバージョンがインストールされている場合は、最新のバージョンにアップグレードできます。 アドイン セットアップ時に既存のバージョンが検出され、更新するかどうかを確認するメッセージが表示されます。 エラー メッセージは、次のようになります。

 **この製品の古いバージョンがシステムで検出されました。既存のインストールをアップグレードしますか?**

 確認すると、アドインの古いバージョンが削除され、新しいバージョンがインストールされます。

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインはインスタンス対応ではありません。 このアドインのインスタンスは 1 台のコンピューターで 1 つだけ実行できます。 異なるバージョンと現在のバージョンとを同時に実行することはできません。

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a>Rscustomaction.exe
 次の表は、rscustomaction.exe スイッチについてまとめたものです。

|Switch|説明|
|------------|-----------------|
|i|カスタム アクションをインストールします。 これにより、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントが SharePoint に登録されます。 W3SVCservice サービスが再起動されます。|
|r|修復|
|u|アンインストール。 これにより、SharePoint ファーム全体から [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの登録が解除されますが、ファイルはディスクに残ります。 W3SVCservice サービスが再起動されます。|
|p|ローカル アンインストール。 これにより、ローカル コンピューターのみから [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの登録が解除されます。 ファイルはディスクに残ります。 W3SVCservice サービスが再起動されます。|
|t|SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 のみ。 レポート サーバーにレポート サーバー データベースに対して機能する接続があるかどうかをテストします。|

## <a name="configuring-reporting-services"></a>Reporting Services の構成
 必要なコンピューターにアドインをインストールしたら、SharePoint サーバーの全体管理からレポート サーバーを構成する必要があります。 必要な手順は、さまざまなテクノロジがインストールされた順序によって異なります。 詳細については、「sharepoint [2010 用 Reporting Services Sharepoint モードをインストールする](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」および「sharepoint[モードのレポートサーバーの Reporting Services &#40;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md) 」を参照してください&#41;

## <a name="see-also"></a>参照
 Sharepoint 2010 [Reporting Services レポートサーバー &#40;Sharepoint モード](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)[の Sharepoint モードをインストール Reporting Services](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)&#41;
