---
title: '[オプション] ([クエリ結果と依存サービス] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d19228fdf17788e9118367a6f0f0eb3be90cb72a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930133"
---
# <a name="options-query-results-and-dependency-services-page"></a>[オプション] ([クエリ結果] および [依存サービス] ページ)
  このページを使用すると、依存サービスのために接続するサーバーを指定できます。 依存サービスを使用すると、異なるサーバーに格納されている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの間の依存関係に関する情報を抽出できます。 オブジェクトの依存関係を表示するには、の [**オブジェクトの依存関係**] ダイアログボックスを使用し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ます。  
  
 **どうしたいんですか。**  
  
1.  [[オプション] ([クエリ結果]/[依存サービス] ページ) ダイアログ ボックスを開く](#open_dialog)  
  
2.  [オプションの構成](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a>[オプション] ([クエリ結果]/[依存サービス] ページ) ダイアログボックスを開く  
  
1.  で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] [**ツール**] メニューの [**オプション**] をクリックします。  
  
2.  **[クエリ結果]** を展開し、**[依存サービス]** をクリックします。  
  
##  <a name="configure-the-options"></a><a name="options"></a>オプションを構成する  
  
### <a name="options"></a>オプション  
 **[依存サービス サーバー]**  
 依存サービスがインストールされているサーバーを指定します。  
  
 **認証**  
 Microsoft Windows ユーザー アカウントを使用してログオンする場合は、[Windows 認証] を選択します。そうでない場合は、[SQL Server 認証] を選択します。  
  
 指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、SQL Server は SQL Server ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。 ログイン アカウントが見つからない場合、認証は失敗し、エラー メッセージが返されます。  
  
 **ユーザー名**  
 SQL Server 認証を使用する場合は、ユーザー名を指定します。  
  
 **パスワード**  
 SQL Server 認証を使用する場合は、パスワードを指定します。  
  
 **テスト**  
 クリックすると、接続がテストされます。