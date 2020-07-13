---
title: SSIS カタログを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2572cc131f34a21171054a159e3b7968c453a780
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437899"
---
# <a name="create-the-ssis-catalog"></a>SSIS カタログの作成
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]でパッケージをデザインしてテストしたら、パッケージを含むプロジェクトを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置できます。 プロジェクトを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置するには、まずサーバーに `SSISDB` カタログを含める必要があります。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] のインストール プログラムでは、カタログは自動的に作成されません。次の手順を使用して、カタログを手動で作成する必要があります。  
  
 SSISDB カタログは [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で作成できます。 Windows PowerShell を使用して、カタログをプログラムから作成することもできます。  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a>SQL Server Management Studio で SSISDB カタログを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開きます。  
  
2.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース エンジンに接続します。  
  
3.  オブジェクト エクスプローラーで、サーバー ノードを展開します。次に、 **[Integration Services カタログ]** ノードを右クリックし、 **[カタログの作成]** をクリックします。  
  
4.  **[CLR 統合を有効にする]** をクリックします。  
  
     カタログは CLR ストアド プロシージャを使用します。  
  
5.  **サーバー インスタンスを再起動するたびに** catalog.startup [ストアド プロシージャが実行されるようにするには、](/sql/integration-services/system-stored-procedures/catalog-startup) [SQL Server のスタートアップ時に Integration Services ストアド プロシージャを自動実行できるようにする] [!INCLUDE[ssIS](../includes/ssis-md.md)] をクリックします。  
  
     このストアド プロシージャは、SSISDB カタログに対する操作の状態のメンテナンスを実行します。 [!INCLUDE[ssIS](../includes/ssis-md.md)] サーバー インスタンスがダウンした場合に、実行されていたパッケージの状態を修正します。  
  
6.  パスワードを入力し、[ **Ok]** をクリックします。  
  
     カタログ データを暗号化するために使用されるデータベース マスター キーがパスワードで保護されます。 パスワードは安全な場所に保管してください。 データベース マスター キーをバックアップすることもお勧めします。 詳細については、「 [データベース マスター キーのバックアップ](../relational-databases/security/encryption/back-up-a-database-master-key.md)」を参照してください。  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a>SSISDB カタログをプログラムから作成するには  
  
1.  次の PowerShell スクリプトを実行します。  
  
    ```powershell
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()
    ```  
  
     Windows PowerShell と <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間の使用方法を紹介したその他の例については、blogs.msdn.com のブログ エントリ「[SQL Server 2012 での SSIS と PowerShell](https://go.microsoft.com/fwlink/?LinkId=242539)」を参照してください。 名前空間とコード例の概要については、blogs.msdn.com のブログ エントリ「 [SSIS カタログ マネージド オブジェクト モデルの概要](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [SSIS カタログ](catalog/ssis-catalog.md)   
 [SSIS カタログのバックアップ、復元、および移動](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
