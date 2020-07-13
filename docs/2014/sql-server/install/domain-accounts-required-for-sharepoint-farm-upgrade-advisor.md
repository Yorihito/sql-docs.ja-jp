---
title: SharePoint ファームに必要なドメインアカウント (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6d68237b2b46147b5e9e5180b7796b5cdb02cee0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054825"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>SharePoint ファームに必要なドメイン アカウント (アップグレード アドバイザー)
  ファーム環境向けに構成されている SharePoint 製品では、ドメイン アカウントを使用する必要があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>説明  
 ファーム環境向けに構成されている SharePoint 製品では、サービスとデータベース接続にドメイン アカウントを使用する必要があります。 これには、Reporting Services サービス アカウントに指定したアカウントも含まれます。  
  
 SharePoint 2010 のサーバーの全体管理ページを使用すると、1 か所で、Reporting Services にドメイン ユーザー アカウントを使用していない場合の問題を確認できます。 Reporting Services 統合の構成を試みると、次のようなエラー メッセージが表示されます。  
  
 "レポート サーバーの実行に使用されているビルトイン NT AUTHORITY\NETWORK SERVICE アカウントは、SharePoint ファームのインストールでサポートされていません。 レポートサーバーを再構成して、ドメインアカウントで実行されるようにしてください。 "  
  
## <a name="corrective-action"></a>修正措置  
 以前のバージョンの場合は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Reporting Services Configuration Manager を使用して、レポートサーバーサービスアカウントとして割り当てられているアカウントを変更します。  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>構成マネージャーでサービス アカウントを変更するには  
  
1.  [**スタート**] メニューの [**すべてのプログラム**] をクリックし、[ **Microsoft SQL Server 2008 R2**] をクリックします。  
  
2.  [**構成ツール**] を選択し、[ **Reporting Services Configuration Manager**] をクリックします。  
  
3.  Configuration Manager で、[**サービスアカウント**] タブを選択します。  
  
4.  [**別のアカウントを使用する**] を選択し、ドメインアカウントの資格情報を入力します。  
  
5.  **[Apply]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
