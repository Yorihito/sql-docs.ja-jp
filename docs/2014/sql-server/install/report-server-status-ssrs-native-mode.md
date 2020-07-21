---
title: レポートサーバーの状態 (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c2fb2860fd80b827e48ad72b59192573d16b8a4d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059078"
---
# <a name="report-server-status-ssrs-native-mode"></a>レポート サーバーの状態 (SSRS ネイティブ モード)
  このページを使用すると、現在接続しているレポート サーバー インスタンスに関する情報を表示できます。 このページはレポート サーバー構成の開始ページです。 他のページでは、URL、サービス アカウント、レポート サーバーのデータベース、レポート サーバーの電子メール配信、スケールアウト配置、および暗号化キーを構成できます。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。  
  
 このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、レポート サーバー インスタンスに接続します。 詳細については、「 [Reporting Services Configuration Manager &#40;del&#41;](reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager (RSConfigTool.exe) は、"highestAvailable" の特権レベルでインストールされます。 この動作は仕様です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API と通信する必要があります。 一部の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通信には、高いレベルまたは管理者の特権が必要です。  
  
 レポート サーバーに接続したときに、すべてのページ リンクがグレー表示されている場合は、レポート サーバー サービスが開始されていることを確認します。 **レポートサービスの状態:** "開始" にする必要があります。 また、サービスの状態を確認するには、管理ツールの [サービス] コンソール アプリケーションを使用します。  
  
## <a name="options"></a>オプション  
 **SQL Server インスタンス**  
 現在接続しているレポート サーバー インスタンスに関する情報が表示されます。 レポート サーバー インスタンスの名前は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスに基づいています。 既定のインスタンスは MSSQLSERVER です。 名前付きインスタンスは、セットアップ中に指定した値になります。 インスタンスの詳細については、オンラインブックの「 [SQL Server の複数のバージョンおよびインスタンスの操作](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
> [!NOTE]  
>  SQL Server Express with Advanced Services の既定のインスタンスは SQLExpress です。  
  
 **インスタンス ID**  
 接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプログラム ファイルを格納する、ファイル システム上のフォルダーに対応します。 **[インスタンス ID]** の値は、セットアップによって *component*.*instance*の形式で割り当てられます。この形式で、 *component* は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを示す値、 *instance* はインスタンス名です。 既定のインスタンス名は MSSQLSERVER です。 たとえば、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンポーネントの既定のインスタンスをインストールした場合、それぞれに対応するフォルダー名は次のようになります。  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 既にインストールされているコンポーネント (など) の2番目のインスタンスをインストールし、そのインスタンスに Contoso という名前を付けた場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] **インスタンス ID**は mssql12.mssqlserver になります。製薬.  
  
 **エディション**  
 エディション情報が表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」を参照してください。  
  
 **製品バージョン**  
 インストールした [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のバージョンが表示されます。  
  
 **レポート サーバー データベース**  
 現在のレポート サーバー インスタンスのアプリケーション データを格納しているレポート サーバー データベースの名前が表示されます。  
  
 **[レポート サーバー モード]**  
 常に値 **Native**が表示されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでサポートされているのはネイティブ モード レポート サーバーだけです。 **[SharePoint 統合モード]** という値が表示されている場合は、ネイティブ モードの配置が正しく構成されていないことを示しています。そのため、ネイティブ モードのレポート カタログに接続する必要があります。 構成マネージャーの **[データベース]** ページを使用してデータベースを変更し、データベースを新規作成するか、ネイティブ モードのレポート サーバーの既存のレポート カタログに接続します。  
  
 **サーバーの状態**  
 レポート サーバー サービスが実行中かどうかを示します。  
  
 **スタート**  
 レポート サーバー サービスを開始します。 たとえば、コンピューター名が変更された後でレポート サーバーを再度構成するときなど、構成を変更した後は、このサービスを再起動する必要があります。 URL 予約を再構成すると、サービスは自動的に再起動されます。 変更を取得するには、サービスを再起動する必要があります。  
  
 **停止**  
 レポート サーバー サービスを停止します。 サービスを停止すると、レポート サーバーの動作が停止します。 詳細については、オンラインブックの「[レポートサーバーサービスの開始および停止](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)」を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
## <a name="see-also"></a>参照  
 [Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Reporting Services Configuration Manager &#40;del&#41;](/sql/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
