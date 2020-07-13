---
title: SQL Server 2014 | の SQL Server Reporting Services における重大な変更Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d86c9bb07a52aba0cd93b006fc33edf4d1aa885
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109933"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2014"></a>SQL Server 2014 における SQL Server Reporting Services の重大な変更
  このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における重大な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするとき、またはカスタムのスクリプトやレポートで発生することがあります。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。  
  
 **このトピックの内容:**  
  
-   [SQL Server 2014 Reporting Services 重大な変更](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services における重大な変更](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services における重大な変更](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-breaking-changes"></a><a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]重大な変更の Reporting Services  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]に重大な変更はありません。  
  
##  <a name="sssql11-reporting-services-breaking-changes"></a><a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]重大な変更の Reporting Services  
  
### <a name="sharepoint-mode-server-references-require-the-sharepoint-site"></a>SharePoint モードのサーバー参照では SharePoint サイトが必要  
 URL パスで仮想ディレクトリ名を使用して、レポート サーバーを直接参照することはできません。 次に例を示します。  
  
 `http://<Server name>/ReportServer`  
  
 URL パスに SharePoint サイトを含める必要があります。 たとえば、サイト名が '`videos`' で、'`sites`' というプレフィックスを使用している場合、URL は次のようになります。  
  
 `http://<Server Name>/sites/videos/_vti_bin/ReportServer`  
  
### <a name="changes-to-sharepoint-mode-command-line-installation"></a>SharePoint モードのコマンド ライン インストールでの変更  
 入力設定 **/RSINSTALLMODE** は、ネイティブ モード インストールでのみ機能し、SharePoint モード インストールでは機能しません。 たとえば、次のはで[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]はサポートされていません: **/RSINSTALLMODE = "defaultsharepointmode"**。 この入力設定の代わりに、 **/RSSHPINSTALLMODE="DefaultSharePointMode"** を使用してください。  
  
 次のステートメントは、完全なインストールコマンドとパラメーターセットの例を示しています。 **setup/ACTION = install/FEATURES = SQL, RS/InstanceName = Denali_INST1.../RSSHPINSTALLMODE = "DefaultSharePointMode"**  
  
 コマンドラインインストールの詳細については、「 [Reporting Services SharePoint モードとネイティブモードのコマンドプロンプトインストール](install-windows/install-reporting-services-at-the-command-prompt.md)」を参照してください。  
  
### <a name="the-reporting-services-wmi-provider-no-longer-supports-configuration-of-sharepoint-mode"></a>Reporting Services WMI プロバイダーでの SharePoint モードの構成操作の廃止  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint の構成は、PowerShell コマンドレットと SharePoint サーバーの全体管理を使用して行うようになりました。 新しい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モード アーキテクチャでは、SharePoint サービス アーキテクチャが使用されます。 SharePoint では、WMI インターフェイスはサポートされません。  
  
 これらの変更によって影響を受けるコンポーネントとワークフローを次に示します。  
  
-   SharePoint モードの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 用に [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI プロバイダーを使用するカスタム アプリケーション。  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャー、rskeymgmt.exe、および rsconfig.exe。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードの構成には、これらのユーティリティの代わりに、SharePoint サーバーの全体管理と PowerShell を使用してください。  
  
-   SQL Server Management Studio: <machine_name>/<instance_name> に似た構文のサーバーを参照することはできません。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] リリース以降では、SharePoint サイト URL を使用する方法が推奨の方法となります。 たとえば、 **http://<sharepoint_server>/<sharePoint_site **>です。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、サポートされる構文は SharePoint サイト URL のみとなります。  
  
### <a name="report-model-designer-is-not-available-in-sql-server-data-tools"></a>レポート モデル デザイナーは SQL Server Data Tools では使用できません  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ではレポート モデル プロジェクトがサポートされなくなりました。 レポート モデル デザイナーは [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]では使用できません。 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、新しいレポート モデル プロジェクトを作成したり、既存のプロジェクトを開いたりすることはできません。また、レポート モデルの作成や更新もできません。 レポート モデルを更新するには、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 以前のツールを使用できます。 レポート モデルは、レポート ビルダーやレポート デザイナーなどの [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] ツールで作成されたレポートでデータ ソースとして使用し続けることができます。 レポート モデルからレポート データを抽出するクエリを作成するために使用したクエリ デザイナーは、引き続き [!INCLUDE[ssSQL11](../includes/sssql11-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で使用できます。  
  
##  <a name="sql-server-2008-r2-reporting-services-breaking-changes"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services 重大な変更  
 ここでは、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における重要な変更について説明します。  
  
> [!NOTE]  
>  SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。  
  
### <a name="expanded-csv-data-renderer"></a>拡張された CSV データ レンダラー  
 で[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]は、CSV ファイルにグラフとゲージのデータが含まれています。 グラフとゲージの列が追加されたため、以前の CSV ファイル構造を使用するアプリケーションは動作しなくなる可能性があります。  
  
 詳細については、「 [CSV ファイルへのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md)で操作できます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 での SQL Server Reporting Services の動作の変更](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [新機能 &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [SQL Server 2014 の SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [SQL Server 2014 で廃止された SQL Server Reporting Services の機能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
