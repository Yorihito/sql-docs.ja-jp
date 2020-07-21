---
title: アプリケーションへの Reporting Services の統合 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ad6d24495bb44a7bd1013dbc822eefe346f02d3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63126151"
---
# <a name="integrating-reporting-services-into-applications"></a>アプリケーションへの Reporting Services の統合
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、拡張性のあるオープンなレポート プラットフォームであり、ソリューションを開発するための API の包括的なセットを開発者に提供するように設計されています。  
  
 カスタム[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アプリケーションに統合するには、レポートサーバー Web サービス ( [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API とも呼ばれます)、の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]ReportViewer コントロール、および URL アクセスの3つのオプションがあります。 アプリケーションに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する方法は、オプションごとに異なります。  
  
## <a name="report-server-web-service"></a>レポート サーバー Web サービス  
 レポート サーバー Web サービスは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して開発を行うための主要なインターフェイスです。 レポート カタログを管理するためのコードを開発する場合でも、サポートされている形式でレポートを表示するためのコードを開発する場合でも、Web サービスでは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアプリケーションに統合するために必要なすべての方法が公開されています。 そのようなアプリケーションの一例が、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に付属のレポート マネージャーです。レポート マネージャーでは、Web サービスを使用してレポート サーバー データベースを管理します。  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Visual Studio の ReportViewer コントロール  
 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] に付属の ReportViewer コントロールは、レポート表示機能をアプリケーションに統合するために使用されます。 コントロールには、Windows フォームベースのアプリケーション用と Web フォームのアプリケーション用の 2 つがあります。 どちらのコントロールにも、レポート サーバーに配置されたレポートを表示する機能と、レポート サーバーがインストールされていない環境にあるレポートを表示する機能があります。  
  
## <a name="url-access"></a>URL アクセス  
 URL アクセスは、ReportViewer コントロールがオプションでない場合にレポート表示機能をアプリケーションに統合するためのもう 1 つのオプションです。 さらに、電子メールを介してユーザーにレポートへのリンクを送信するためにも使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SOAP を使用した Reporting Services の統合](../application-integration/integrating-reporting-services-using-soap.md)  
 レポート サーバー Web サービスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションおよび管理を既存のビジネス アプリケーションに統合する方法について説明します。  
  
 [ReportViewer コントロールを使用した Reporting Services の統合](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 ReportViewer コントロールを使用して、レポート表示機能を既存のアプリケーションに統合する方法について説明します。  
  
 [URL アクセスを使用した Reporting Services の統合](../application-integration/integrating-reporting-services-using-url-access.md)  
 URL アクセスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションを既存のビジネス アプリケーションに統合する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [URL アクセスと SOAP の選択](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [SSRS&#41;&#40;テクニカルリファレンス](../../../2014/reporting-services/technical-reference-ssrs.md)   
 [レポート サーバー web サービス](../report-server-web-service/report-server-web-service.md)  
  
  
