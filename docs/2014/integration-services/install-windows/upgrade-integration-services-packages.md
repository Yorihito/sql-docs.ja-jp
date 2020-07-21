---
title: Integration Services パッケージのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, migrating
- migrating packages [Integration Services]
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 447d880fb80871dbb3de46b389be6b1937f64a99
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968372"
---
# <a name="upgrade-integration-services-packages"></a>Integration Services パッケージのアップグレード
  またはのインスタンスを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] の現在のリリースにアップグレードすると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、既存の [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] パッケージは、現在のリリースで使用されているパッケージ形式に自動的にアップグレードされません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。 アップグレード方法を選択して、パッケージを手動でアップグレードする必要があります。  
  
 パッケージをアップグレードすると [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、によって、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 任意のスクリプトタスクおよびスクリプトコンポーネントのスクリプトが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] TOOLS for Applications (VSTA) に移行されます。 では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、スクリプトタスクまたはスクリプトコンポーネント内のスクリプトは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] アプリケーション (VSA) に使用されます。 移行前に必要となる可能性があるスクリプトへの変更やスクリプトの変換エラーに関する詳細については、「[VSTA へのスクリプトの移行](../../sql-server/install/migrate-scripts-to-vsta.md)」を参照してください。  
  
 プロジェクトをプロジェクトの配置モデルに変換する際のパッケージのアップグレードについては、「 [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md)」を参照してください。  
  
## <a name="sql-server-2000-data-transformation-services-packages"></a>SQL Server 2000 データ変換サービス パッケージ  
 現在のリリースのでは、データ変換サービス (DTS) パッケージの移行または実行のサポートは廃止されました [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。 次の DTS 機能は廃止されました。  
  
-   DTS ランタイム  
  
-   DTS API  
  
-   DTS パッケージを次期バージョンの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   DTS パッケージのメンテナンス機能のサポート [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   DTS 2000 パッケージ実行タスク  
  
-   アップグレード アドバイザーによる DTS パッケージのスキャン  
  
 DTS パッケージを移行する場合は、次のオプションがあります。  
  
-   パッケージを [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] または [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] に移行し、その後でパッケージを [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] にアップグレードする。  
  
     [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] と [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] に DTS パッケージを移行する方法の詳細については、「[データ変換サービス パッケージの移行](https://go.microsoft.com/fwlink/?LinkId=251870)」(2005) および「[データ変換サービス パッケージの移行](https://go.microsoft.com/fwlink/?LinkId=251871)」(2008) を参照してください。  
  
-   [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] を使用して DTS パッケージを再作成する。  
  
     [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] の新機能については、「[新機能 &#40;Integration Services&#41;](../what-s-new-in-integration-services-in-sql-server-2016.md)」を参照してください。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの構造の概要については、「[Integration Services &#40;SSIS&#41; パッケージ](../integration-services-ssis-packages.md)」を参照してください。  
  
## <a name="selecting-an-upgrade-method"></a>アップグレード方法の選択  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] パッケージは、さまざまな方法でアップグレードできます。 その方法によって、アップグレードが一時的な場合と 永続的な場合があります。 次の表に、それらの各方法とアップグレードが一時的か永続的かを示します。  
  
> [!NOTE]  
>  現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と共にインストールされる **dtexec** ユーティリティ (dtexec.exe) を使用して [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]または [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] パッケージを実行すると、一時パッケージのアップグレードが行われることで、実行時間が増加します。 パッケージ実行時間の増加比率は、パッケージのサイズに応じて異なります。 実行時間が増加しないようにするには、パッケージの実行前にアップグレードしておくことをお勧めします。  
  
|アップグレード方法|アップグレードの種類|  
|--------------------|---------------------|  
|現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と共にインストールされる **dtexec** ユーティリティ (dtexec.exe) を使用して、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] または [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] パッケージを実行します。<br /><br /> 詳細については、「[dtexec ユーティリティ](../packages/dtexec-utility.md)」を参照してください。|パッケージのアップグレードは一時的です。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パッケージでは、スクリプトの移行は一時的です。<br /><br /> 変更を保存することはできません。|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] パッケージ ファイルを開きます。|パッケージのアップグレードは、パッケージを保存した場合は永続的になり、パッケージを保存しなかった場合は一時的になります。<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パッケージでは、スクリプトの移行は、パッケージを保存した場合は永続的になり、パッケージを保存しなかった場合は一時的になります。|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] または [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] パッケージを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の既存のプロジェクトに追加します。|パッケージのアップグレードは永続的です。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パッケージでは、スクリプトの移行は永続的です。|  
|[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] で [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] または [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロジェクト ファイルを開き、[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを使用してプロジェクト内の複数のパッケージをアップグレードします。<br /><br /> 詳細については、「 [SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード](upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md) 」および [SSIS パッケージ アップグレード ウィザードの F1 ヘルプ](../ssis-package-upgrade-wizard-f1-help.md)」を参照してください。|パッケージのアップグレードは永続的です。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パッケージでは、スクリプトの移行は永続的です。|  
|現在のリリースの <xref:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade%2A> メソッドを使用して、1 つまたは複数の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、さまざまな方法でアップグレードできます。|パッケージのアップグレードは永続的です。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パッケージでは、スクリプトの移行は永続的です。|  
  
## <a name="custom-applications-and-custom-components"></a>カスタム アプリケーションおよびカスタム コンポーネント  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、 カスタム コンポーネントが動作しません。  
  
 現在のリリースのツールを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] およびカスタムコンポーネントを含むパッケージを実行および管理でき [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] ます。 ランタイム アセンブリを Version 10.0.0.0 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]) から Version 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) にリダイレクトする際に役立つ 4 つのバインド リダイレクト ルールが次のファイルに追加されました。  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 を使用し [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] て、カスタムコンポーネントを含むパッケージを設計するに [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] : common7\ide にあるファイルを devenv.exe.config 変更する必要があり *\<drive>* ます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のランタイムで構築された顧客アプリケーションでこれらのパッケージを使用するには、実行可能ファイルに対応する *.exe.config ファイルの configuration セクションにリダイレクト ルールを含めます。 これらのルールにより、ランタイム アセンブリが Version 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) にリダイレクトされます。 アセンブリバージョンのリダイレクトの詳細については、「」 [ \<assemblyBinding> の \<runtime> 要素](https://msdn.microsoft.com/library/twy1dw1e.aspx)を参照してください。  
  
### <a name="locating-the-assemblies"></a>アセンブリの場所  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] アセンブリが .NET 4 にアップグレードされました。 .NET 4 用の個別のグローバルアセンブリキャッシュがあります。これは、\Windows\ microsoft.net \assembly にあり *\<drive>* ます。 すべての [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] アセンブリは、通常、このパスの GAC_MSIL フォルダーにあります。  
  
 以前のバージョンのと同様に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、コア [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 機能拡張 .dll ファイルは次の場所にもあります *\<drive>* : server\100\sdk\assemblies  
  
## <a name="understanding-sql-server-package-upgrade-results"></a>SQL Server パッケージのアップグレード結果について  
 パッケージのアップグレード プロセス中に、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] パッケージ内のほとんどのコンポーネントと機能が、現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の対応するコンポーネントと機能にシームレスに変換されます。 ただし、いくつかのコンポーネントと機能については、アップグレードされないか、アップグレード結果に注意が必要です。 それらのコンポーネントと機能を次の表に示します。  
  
> [!NOTE]  
>  この表の一覧に示された問題を含むパッケージを識別するには、アップグレード アドバイザーを実行します。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。  
  
|コンポーネントまたは機能|アップグレード結果|  
|--------------------------|---------------------|  
|Connection strings|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] パッケージでは、特定のプロバイダーの名前が変更されているため、接続文字列の値を変更する必要があります。 接続文字列を更新するには、次のいずれかの手順を実行します。<br /><br /> - [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージアップグレードウィザードを使用してパッケージをアップグレードし、[**新しいプロバイダー名を使用するための接続文字列を更新**する] オプションを選択します。<br /><br /> -の [ [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] オプション] ダイアログボックスの [全般] ページで、[**新しいプロバイダー名を使用する接続文字列を更新する**] オプションを選択します。 このオプションの詳細については、「 [[全般] ページ](../general-page-of-integration-services-designers-options.md)」を参照してください。<br /><br /> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でパッケージを開き、ConnectionString プロパティのテキストを手動で変更します。<br /><br /> 注: 接続文字列が構成ファイルまたはデータ ソース ファイルに格納されている場合、または式で `ConnectionString` プロパティを設定する場合は、上記の手順を使用して接続文字列を更新することはできません。 このような場合に接続文字列を更新するには、ファイルまたは式を手動で更新する必要があります。<br /><br /> 使用できるデータ ソースの詳細については、「 [データ ソース](../connection-manager/data-sources.md)」を参照してください。|  
|参照変換|パッケージの場合 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、アップグレードプロセスでは、参照変換がの現在のリリースに自動的にアップグレードされ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。 ただし、現在のリリースのこのコンポーネントには、それ以外にも利用できる機能がいくつか追加されています。<br /><br /> 詳細については、「[参照変換](../data-flow/transformations/lookup-transformation.md)」を参照してください。|  
|スクリプト タスクとスクリプト コンポーネント|スクリプト タスクおよびスクリプト コンポーネント内のスクリプトは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パッケージのアップグレード プロセスで VSA から VSTA に自動的に移行されます。<br /><br /> 移行前に必要となる可能性があるスクリプトへの変更やスクリプトの変換エラーに関する詳細については、「[VSTA へのスクリプトの移行](../../sql-server/install/migrate-scripts-to-vsta.md)」を参照してください。|  
  
### <a name="scripts-that-depend-on-adodbdll"></a>ADODB.dll に依存するスクリプト  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がインストールされていないコンピューターでは、ADODB.dll を明示的に参照するスクリプト タスクおよびスクリプト コンポーネントのスクリプトをアップグレードしたり、実行したりすることはできません。 このようなスクリプト タスクまたはスクリプト コンポーネントのスクリプトをアップグレードするには、ADODB.dll に対する依存関係を削除することをお勧めします。  また、VB や C# のスクリプトなどのマネージド コードの代わりに ADO.NET を使用することをお勧めします。  
  
## <a name="external-resources"></a>外部リソース  
  
-   msdn.microsoft.com の技術記事「[SSIS から SQL Server 2012 へのスムーズなアップグレードのための 5 つのヒント](https://go.microsoft.com/fwlink/?LinkId=235321)」  
  
-   blogs.msdn.com のブログ記事「 [既存のカスタムSSIS拡張機能とアプリケーションをデナリで動作させる](https://go.microsoft.com/fwlink/?LinkId=238157)」  
  
-   channel9.msdn.com の Web キャスト「[Upgrading SSIS Packages to SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=258674)」  
  
  
