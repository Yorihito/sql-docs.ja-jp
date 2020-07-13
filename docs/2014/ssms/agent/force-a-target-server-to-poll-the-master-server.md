---
title: ターゲット サーバーからのマスター サーバーのポーリングの強制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
ms.openlocfilehash: 307eee715b468c3d99fa0b8e1779ba2c6c73cbaf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008751"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>ターゲット サーバーからのマスター サーバーのポーリングの強制
  このトピックでは、ターゲット サーバーからマスター サーバーにポーリングさせる方法について説明します。 ターゲット サーバーは、マスター サーバーの登録済みサーバーである必要があります。  
  
 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。 マルチサーバー ジョブとは、1 つ以上のターゲット サーバーでマスター サーバーにより実行されるジョブです。 各ターゲット サーバーは、同じジョブのインスタンスを同時に実行できます。 各ターゲット サーバーからマスター サーバーに定期的にポーリングし、そのターゲット サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。 ダウンロードされたジョブはターゲット サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。  
  
> [!NOTE]  
>  ターゲット サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#Restrictions)、 [セキュリティ](#Security)  
  
-   **ターゲット サーバーからマスター サーバーにポーリングさせるために使用するもの:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
 ターゲット サーバーは、マスター サーバーの登録済みサーバーである必要があります。 このトピックに説明されている手順は、マスター サーバーから実行する必要があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 」および「 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
 **ターゲット サーバーからマスター サーバーにポーリングさせるには**  
  
1.  **オブジェクト エクスプローラー**で、マスター サーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** をクリックします。  
  
3.  ターゲット サーバーをクリックし、**[強制的にポーリング]** をクリックします。  
  
  
