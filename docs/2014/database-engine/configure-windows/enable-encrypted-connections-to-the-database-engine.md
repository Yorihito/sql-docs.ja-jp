---
title: データベースエンジンへの暗号化接続を有効にします (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e6e45b1f49c348e6cce329fb918479e92edbe9ae
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935341"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a>データベース エンジンへの暗号化接続の有効化 (SQL Server 構成マネージャー)
  このトピックでは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 構成マネージャーを使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] の証明書を指定することにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの暗号化接続を有効にする方法について説明します。 サーバー コンピューターには証明書を提供し、クライアント マシンは証明書のルート機関を信頼するように設定する必要があります。 提供は、証明書を Windows にインポートすることでインストールする処理です。  
  
 **サーバー認証**用の証明書が発行されている必要があります。 証明書の名前は、コンピューターの完全修飾ドメイン名 (FQDN) である必要があります。  
  
 証明書は、コンピューター上のユーザーにローカルに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用するための証明書をインストールするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスと同じユーザー アカウントを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを実行する必要があります。ただし、LocalSystem、NetworkService、または LocalService でサービスが実行されていて、管理者アカウントを使用している場合を除きます。  
  
 クライアントは、サーバーが使用する証明書の所有権を検証できる必要があります。 サーバー証明書に署名した証明機関の公開キー証明書をクライアントが持っている場合は、それ以上の構成は必要ありません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows には、多くの証明機関の公開キー証明書が含まれています。 サーバー証明書に署名した公的または私的な証明機関に対する公開キー証明書をクライアントが持っていない場合は、サーバー証明書に署名した証明機関の公開キー証明書をインストールする必要があります。  
  
> [!NOTE]  
>  フェールオーバー クラスターで暗号化を使用する場合、フェールオーバー クラスター内のすべてのノードに対して、仮想サーバーの完全修飾 DNS 名を使用してサーバー証明書をインストールする必要があります。 たとえば、"test1." という名前のノードを持つ2ノードクラスターがあると *\<your company>* します。com と *\<your company>* test2.また、仮想サーバーを仮想サーバーとして使用している場合は、仮想サーバーをインストールする必要があり *\<your company>* ます。両方のノードの com。 **[ForceEncryption]** オプションの値を **[はい]** に設定できます。  
  
 **このトピックの内容**  
  
-   **暗号化された接続を有効にするには:**  
  
     [サーバーに証明書を提供 (インストール) する](#Provision)  
  
     [サーバー証明書をエクスポートする](#Export)  
  
     [暗号化された接続を許可するサーバーを構成する](#ConfigureServerConnections)  
  
     [暗号化された接続を要求するクライアントを構成する](#ConfigureClientConnections)  
  
     [SQL Server Management Studio から接続を暗号化する](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> サーバーに証明書を提供 (インストール) するには  
  
1.  [**スタート**] メニューの [ファイルの**実行**] をクリックし、[**名前**] ボックスに「」と入力して、 `MMC` [ **OK**] をクリックします。  
  
2.  MMC コンソールで、[**ファイル**] メニューの [**スナップインの追加と削除**] をクリックします。  
  
3.  **[スナップインの追加と削除]** ダイアログ ボックスで **[追加]** をクリックします。  
  
4.  **[スタンドアロン スナップインの追加]** ダイアログ ボックスで **[証明書]** をクリックし、次に **[追加]** をクリックします。  
  
5.  **[証明書スナップイン]** ダイアログ ボックスで **[コンピューター アカウント]** をクリックし、 **[完了]** をクリックします。  
  
6.  **[スタンドアロン スナップインの追加]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
7.  **[スナップインの追加と削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
8.  **[証明書]** スナップインで、 **[証明書]**、 **[個人]** の順に展開し、 **[証明書]** を右クリックします。次に **[すべてのタスク]** をポイントし、 **[インポート]** をクリックします。  
  
9. **[証明書のインポート ウィザード]** を完了して証明書をコンピューターに追加し、MMC コンソールを閉じます。 コンピューターへの証明書の追加の詳細については、Windows のマニュアルを参照してください。  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a> サーバー証明書をエクスポートするには  
  
1.  **[証明書]** スナップインで、 **[証明書]** / **[個人]** フォルダーで証明書を探し、 **[証明書]** を右クリックします。次に **[すべてのタスク]** をポイントし、 **[エクスポート]** をクリックします。  
  
2.  **証明書のエクスポート ウィザード**を実行して、証明書ファイルを使いやすい場所に格納します。  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> 暗号化された接続を許可するサーバーを構成するには  
  
1.  **SQL Server 構成マネージャー**で、[**ネットワークの構成**] を SQL Server 展開し、[**のプロトコル**] を右クリックして、[ _\<server instance>_ **プロパティ**] を選択します。  
  
2.  [プロパティ**のプロトコル** _\<instance name>_ **Properties** ] ダイアログボックスの [**証明書**] タブで、[**証明**書] ボックスの一覧から目的の証明書を選択し、[ **OK]** をクリックします。  
  
3.  **[フラグ]** タブの **[ForceEncryption]** ボックスの一覧の **[はい]** をクリックし、 **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再開します。  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a> 暗号化された接続を要求するクライアントを構成するには  
  
1.  元の証明書ファイルまたはエクスポートした証明書ファイルを、クライアント コンピューターにコピーします。  
  
2.  クライアント コンピューターで、 **証明書** スナップインを使用して、ルート証明書またはエクスポートした証明書ファイルをインストールします。  
  
3.  コンソール ペインで **[SQL Server Native Client の構成]** を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  **[フラグ]** ページの **[プロトコルの暗号化を設定する]** ボックスで、 **[はい]** をクリックします。  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a> SQL Server Management Studio から接続を暗号化するには  
  
1.  オブジェクト エクスプローラー ツール バーで **[接続]** をクリックし、 **[データベース エンジン]** をクリックします。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスで接続情報を入力し、 **[オプション]** をクリックします。  
  
3.  **[接続のプロパティ]** タブで **[暗号化接続]** をクリックします。  
  
  
