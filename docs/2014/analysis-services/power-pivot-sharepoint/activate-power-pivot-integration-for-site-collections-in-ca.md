---
title: サーバーの全体管理でサイトコレクションの PowerPivot 機能の統合をアクティブにする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b479564984727e47432754d0a660e6aa979244b3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547634"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>サイト コレクションを対象とした PowerPivot 機能の統合をサーバーの全体管理でアクティブ化する方法
  [既存のファーム] インストール オプションを使用して SQL Server PowerPivot for SharePoint をインストールした場合は、サイト コレクションごとに PowerPivot 機能の統合をアクティブ化する必要があります。 [新しいサーバー] インストール オプションを使用して PowerPivot for SharePoint をインストールした場合は、この作業は必要ありません。このオプションでは、SQL Server セットアップで配置を構成するときに、PowerPivot 機能の統合がルート サイト コレクションに対してアクティブ化されます。  
  
 サイトでアプリケーション ページやテンプレートを使用できるようにするには、サイト コレクション レベルで機能をアクティブ化する必要があります。これには、定期データを更新するための構成ページや、PowerPivot ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。  
  
 PowerPivot 統合は、PowerPivot クエリ処理をサポートするサイト コレクションごとにアクティブ化する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 サイト コレクション管理者である必要があります。  
  
## <a name="activate-powerpivot-features"></a>PowerPivot 機能のアクティブ化  
  
1.  SharePoint サイトで、 **[サイトの操作]** をクリックします。  
  
     既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 したがって、多くの場合、「http://\<computer name>」と入力してルート サイト コレクションを開くことで SharePoint サイトにアクセスできます。  
  
2.  **[サイトの設定]** をクリックします。  
  
3.  [サイト コレクションの管理] で **[サイト コレクションの機能]** をクリックします。  
  
4.  [ **PowerPivot 統合サイトコレクション機能**] が表示されるまでページを下にスクロールします。  
  
5.  **[アクティブ化]** をクリックします。  
  
6.  他のサイト コレクションについても、各サイトを開き、 **[サイトの操作]** をクリックして手順を繰り返します。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [初期構成 &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
