---
title: SharePoint モードの Reporting Services のハードウェアとソフトウェアの要件 |Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c1f95544de8f0362b8981a175f1c65de1798a1eb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059319"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a>Reporting Services の SharePoint モードに関するハードウェアとソフトウェアの要件

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SharePoint モードで実行するための前提条件、ハードウェア要件、およびインストールに関する考慮事項について説明し [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードには SharePoint Server が必要なため、要件のほとんどは SharePoint 環境に基づきます。 ネイティブ モード レポート サーバーの場合、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を実行するための最低限のハードウェア要件とソフトウェア要件をハードウェアが満たしている必要があります。 詳細については、「 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)」をご参照ください。  
  
-   [必須コンポーネント](#bkmk_prereq)  
  
-   [レポートサーバーデータベースの要件](#bkmk_report_server_database)  
  
-   [Power View の要件](#bkmk_powerview)  
  
-   [その他の情報](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> 必要条件  
  
-   ローカル インストールの場合は、SharePoint と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール時にログインしたアカウントは、ローカルのオペレーティング システムの Administrators グループのメンバーである必要があります。 セットアップ アカウントは、SharePoint ファーム管理者グループのメンバーである必要はありません。  
  
     詳細については、「 [SharePoint 2013 のアカウントのアクセス許可とセキュリティ設定](https://technet.microsoft.com/library/cc678863.aspx)」を参照してください。  
  
-   SharePoint モードで実行している [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、SharePoint サーバーが必要です。 SharePoint の要件および構成の詳細については、以下を参照してください。  
  
    -   [ハードウェアとソフトウェアの要件 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)  
  
    -   [SharePoint Server 2013 の容量管理およびサイズ変更](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [ビジネス インテリジェンスのソフトウェア要件 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [ハードウェア要件およびソフトウェア要件 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [SharePoint Server 2010 の容量管理およびサイズ変更](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用して既存の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]SharePoint インストールをアップグレードまたは更新する場合は、「 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)を実行するための最低限のハードウェア要件とソフトウェア要件をハードウェアが満たしている必要があります。  
  
-   **SharePoint 2013 Administration** Service が開始されていることを Windows サーバー マネージャーで確認します。  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a> レポート サーバー データベースの要件  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および SharePoint 製品とテクノロジはどちらも、SQL Server のリレーショナル データベースを使用して、アプリケーション データを格納します。  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] には、互換性のある SQL Server エディションの [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスが必要です。 ハードウェアとソフトウェアの要件の詳細については、「 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。  
  
-   SharePoint 製品では、既存のデータベース インスタンスを使用できます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスがインストールされていない場合、SharePoint 製品のセットアップ プログラムでは SharePoint アプリケーションのデータベース用に SQL Server Express Edition がインストールされます。  
  
-   レポート サーバー インスタンスの場合、データベースに SQL Server Express Edition を使用することはできません。 ただし、SharePoint 製品によってインストールされる SQL Server Express Edition インスタンスは、他のデータベース エンジン エディションと共存できます。  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a>[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]要件

 Office.Microsoft.com で最新の [Power View 関連ドキュメント](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) を確認してください。 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] は Microsoft Excel 2013 の機能の 1 つであり、Microsoft SharePoint Server 2010 および 2013 の Enterprise Edition 用の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services アドインに含まれています。  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> その他の情報

 SharePoint の変更の詳細については、「 [sharepoint 2010 から sharepoint 2013 への変更](https://technet.microsoft.com/library/ff607742\(office.15\).aspx)()」を参照してください https://technet.microsoft.com/library/ff607742(office.15).aspx) 。  
  
 [SQL Server 2014 リリースノート](https://go.microsoft.com/fwlink/?LinkID=296445)。  
  
