---
title: データベース (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4fc3fdb873a567bef9326232e5435cea5649b041
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054875"
---
# <a name="database-ssrs-native-mode"></a>データベース (SSRS ネイティブ モード)
  [データベース] ページを使用すると、1 つまたは複数のレポート サーバー インスタンスに対して内部記憶域を提供するレポート サーバー データベースの作成や構成を行うことができます。 リモートのレポート サーバー データベースが使用されるようにレポート サーバーを構成する場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してデータベースを作成する必要があります。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。  
  
 レポート サーバー データベースの作成と接続の構成は複数の手順から成る作業です。 このページには、タスクごとに各手順を示すウィザードが用意されています。 権限およびログインの作成または更新も行えます。 [進行状況] ページでは、各手順の状態を監視できます。 エラーが発生した場合は、そのエラーをクリックすることで、エラーの解決方法に関する情報を表示できます。  
  
 レポート サーバー データベースでは、特定のサーバー モードをサポートする必要があります。 既定のモードはネイティブ モードですが、SharePoint の製品またはテクノロジの大規模な配置でレポート サーバーを実行している場合は、SharePoint 統合モード用のレポート サーバー データベースを作成することもできます。 詳細については、「[ネイティブ モードのレポート サーバー データベースの作成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)」を参照してください。  
  
 このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウで **[データベース]** をクリックします。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **SQL Server 名**  
 [現在のレポート サーバー データベース] の **[SQL Server 名]** では、レポート サーバー データベースを実行する [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] の名前を指定します。 ローカルまたはリモートのコンピューターの、既定または名前付きのインスタンスを使用できます。  
  
 **データベース名**  
 サーバー データを格納するレポート サーバー データベースの名前を指定します。  
  
 **[レポート サーバー モード]**  
 レポート サーバー データベースでネイティブ モードと SharePoint 統合モードのどちらをサポートするかを示します。 詳細については、「[レポートサーバーの Reporting Services](../../../2014/reporting-services/reporting-services-report-server.md)」を参照してください。  
  
 **データベースの変更**  
 レポート サーバー データベースの作成または選択に必要なすべての手順を示すウィザードを起動します。  
  
 **資格情報の種類**  
 レポート サーバーがレポート サーバー データベースへの接続に使用する資格情報を指定します。 指定できる資格情報の種類には、サービス アカウント、Windows ドメイン ユーザー、Windows ローカル ユーザー、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインがあります。 資格情報の選択の詳細については、「 [SSRS Configuration Manager&#41;&#40;レポートサーバーデータベース接続の構成](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。  
  
 **ユーザー名**  
 Windows 資格情報を使用している場合はドメイン ユーザー アカウントを指定し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報を使用している場合は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。 Windows 資格情報を使用している場合は、 * \<domain> \\<アカウント \> *の形式で指定します。  
  
 **パスワード**  
 アカウントのパスワードを指定します。  
  
 **資格情報の変更**  
 別のアカウントを選択したり、レポート サーバー データベースへの接続に使用するアカウントのパスワードを更新するのに必要なすべての手順を示すウィザードを起動します。  
  
## <a name="see-also"></a>参照  
 [SSRS Configuration Manager &#40;ネイティブモードのレポートサーバーデータベースを作成&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [レポートサーバーデータベース &#40;SSRS ネイティブモード&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
