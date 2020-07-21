---
title: サーバーの登録
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c6008c1d719fa7c452bb64c51fa573432e0ce4c0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058410"
---
# <a name="register-servers"></a>サーバーの登録
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にサーバーを登録することで、サーバー接続情報を保存して、その後の接続時に使用できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]にサーバーを登録するには、次の 3 とおりの方法があります。  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のインストール後の最初の起動時に、自動的に登録されます。  
  
2.  また、この自動登録プロセスはいつでも開始でき、ローカル サーバー インスタンスの登録を復元できます。  
  
3.  さらに、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の登録済みサーバー ツールを使用してサーバーを登録できます。  
  
## <a name="benefits-of-registered-servers"></a>登録済みサーバーの利点  
 登録済みサーバーを使用して、以下の操作を行うことができます。  
  
-   接続情報を保存するためにサーバーを登録できます。  
  
-   登録済みサーバーが実行中かどうかを判別できます。  
  
-   オブジェクト エクスプローラーとクエリ エディターを登録済みサーバーに簡単に接続できます。  
  
-   登録済みサーバーの登録情報の編集や削除を行えます。  
  
-   サーバーのグループを作成できます。  
  
-   **[登録済みサーバーの名前]** ボックスに **[サーバー名]** 一覧とは別の値を指定して、登録済みサーバーにわかりやすい名前を設定できます。  
  
-   登録済みサーバーの詳細な説明を設定できます。  
  
-   登録済みサーバーのグループの詳細な説明を設定できます。  
  
-   登録済みサーバーのグループをエクスポートできます。  
  
-   登録済みサーバーのグループをインポートできます。  
  
-   オンラインまたはオフラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルを表示できます。  
  
## <a name="related-tasks"></a>Related Tasks  
 登録したサーバーの基礎知識については、次の各トピックを参照してください。  
  
|**説明**|**トピック**|  
|---------------------|---------------|  
|ローカル サーバー インスタンスの登録|[接続済みのサーバーの登録 &#40;SQL Server Management Studio&#41;](register-a-connected-server-sql-server-management-studio.md)|  
|サーバーの登録|[新しい登録済みサーバーの作成 &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)|  
|登録済みサーバーの表示|[SQL Server Management Studio で登録済みサーバーを表示する方法](view-registered-servers-in-sql-server-management-studio.md)|  
|登録済みサーバーの削除|[新しい登録済みサーバーの削除 &#40;SQL Server Management Studio&#41;](remove-a-registered-server-sql-server-management-studio.md)|  
|サーバーの登録の変更|[サーバーの登録の変更 &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md)|  
|登録済みサーバーの接続|[登録済みサーバーへの接続 &#40;SQL Server Management Studio&#41;](connect-to-a-registered-server-sql-server-management-studio.md)|  
|登録済みサーバーの切断|[登録済みサーバーの切断 &#40;SQL Server Management Studio&#41;](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|登録済みサーバーまたはサーバー グループの移動|[登録済みサーバーまたは登録済みサーバー グループの移動 &#40;SQL Server Management Studio&#41;](move-a-registered-server-or-registered-server-group.md)|  
|登録済みサーバーまたはサーバー グループの名前変更|[登録済みサーバーまたは登録済みサーバー グループの名前の変更 &#40;SQL Server Management Studio&#41;](change-the-name-of-registered-server-or-registered-server-group.md)|  
|サーバー グループの作成または編集|[サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|サーバー グループの削除|[サーバー グループの削除 &#40;SQL Server Management Studio&#41;](remove-a-server-group-sql-server-management-studio.md)|  
|登録済みサーバーの情報のエクスポート|[登録済みサーバー情報のエクスポート &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md)|  
|登録済みサーバーの情報のインポート|[登録済みサーバー情報のインポート &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)|  
|中央管理サーバーおよびサーバー グループの作成|[中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)|  
|複数のサーバーに対するステートメントの同時実行|[複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a>参照  
 [リモート サーバー](../../database-engine/configure-windows/remote-servers.md)  
  
  
