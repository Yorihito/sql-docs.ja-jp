---
title: 緊急時のオペレーターを指定する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73eb11034d185deb9c004d138230fff8fbf27bb6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995290"
---
# <a name="designate-a-fail-safe-operator"></a>Designate a Fail-Safe Operator
  緊急時のオペレーターとは、指定オペレーターが不在の場合に警告を受信するユーザーのことです。 このトピックでは、を使用して、でエージェントの警告通知を受信する緊急時のオペレーターを設定する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **緊急時のオペレーターを指定する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   ポケットベルと**net send**のオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の将来のバージョンでエージェントから削除される予定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] です。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。  
  
-   SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。 詳細については、「 [オペレーターへの警告の割り当て](assign-alerts-to-an-operator.md)」を参照してください。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 緊急時のオペレーターを指定できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-designate-a-fail-safe-operator"></a>緊急時のオペレーターを指定するには  
  
1.  **オブジェクト エクスプローラー** で、緊急時のオペレーターとして指定する SQL Server エージェント オペレーターを含むサーバーをプラス記号をクリックして展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。  

3.  [ **SQL Server エージェントのプロパティ-**_server_name_ ] ダイアログボックスの [**ページの選択**] で、[**警告システム**] を選択します。  
 
4.  **[緊急時のオペレーター]** の **[緊急時のオペレーターを有効にする]** チェック ボックスをオンにします。  
  
5.  **[オペレーター]** 一覧から、緊急時のオペレーターにするオペレーターを選択します。  
  
6.  **[電子メール]**、 **[ポケットベル]**、 **[Net send]** チェック ボックスのいずれかまたはすべてを選択して、オペレーターへの通知方法を指定します。  
  
7.  完了したら、[**OK**] をクリックします。  
  
  
