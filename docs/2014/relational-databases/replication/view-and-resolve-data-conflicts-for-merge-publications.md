---
title: マージパブリケーションのデータの競合の表示および解決 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77aa9ece0073149c017f6eca35a756b22751a74b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063668"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications-sql-server-management-studio"></a>マージ パブリケーションでのデータの競合の表示および解決 (SQL Server Management Studio)
  マージ レプリケーションの競合は、各アーティクルに対して指定された競合回避モジュールに基づいて解決されます。 既定では、競合はユーザーの介入を必要とせずに解決されます。 ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] レプリケーション競合表示モジュールで競合を表示したり、解決の結果を変更したりすることができます。  
  
 競合データは、競合の保有期間に指定した期間内 (既定では 14 日間) はレプリケーション競合表示モジュールで利用できます。 競合の保有期間を設定するには、次のいずれかを実行します。  
  
-   **@conflict_retention** [Sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)のパラメーターの保有期間の値を指定します。  
  
-   パラメーターに**conflict_retention**の値を指定 **@property** し、 **@value** [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)のパラメーターに保有期間の値を指定します。  
  
 競合情報の既定の保存先は次のとおりです。  
  
-   パブリケーションの互換性レベルが 90 RTM 以上の場合は、パブリッシャーおよびサブスクライバーに保存されます。  
  
-   パブリケーションの互換性レベルが 80 RTM 未満の場合は、パブリッシャーに保存されます。  
  
-   サブスクライバーが [!INCLUDE[ssEW](../../includes/ssew-md.md)]を実行している場合は、パブリッシャーに保存されます。 競合データを [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーに保存することはできません。  
  
 競合情報を格納する領域は、 **conflict_logging** パブリケーション プロパティによって制御されます。 詳細については、「[sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)」と「[sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)」をご覧ください。  
  
 競合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインタラクティブ競合回避モジュールを使用して、同期実行時に対話的に解決することもできます。 インタラクティブ競合回避モジュールは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーで利用できます。 詳細については、「[Windows 同期マネージャーを使用したサブスクリプションの同期 &#40;Windows 同期マネージャー&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)」をご覧ください。  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a>マージ パブリケーションで競合を表示および解決するには  
  
1.  でパブリッシャー (または必要に応じてサブスクライバー) に接続 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] し、サーバーノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  競合を表示するパブリケーションを右クリックしてから、 **[競合の表示]** をクリックします。  
  
    > [!NOTE]  
    >  **conflict_logging** プロパティの値として **'subscriber'** を指定した場合は、 **[競合の表示]** メニュー オプションを利用できません。 競合を表示するには、コマンド プロンプトで ConflictViewer.exe を起動します。 既定では、ConflictViewer.exe が格納されているディレクトリは、Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE です。 有効な起動時のパラメーターの一覧を表示するには、ConflictViewer.exe -? を実行します。  
  
4.  **[競合テーブルの選択]** ダイアログ ボックスで、競合を表示するデータベース、パブリケーション、およびテーブルを選択します。  
  
5.  レプリケーション競合表示モジュールでは、以下を実行できます。  
  
    -   上のグリッドの右側のボタンで行をフィルター選択する。  
  
    -   上のグリッドで行を選択して、下のグリッドにその行の情報を表示する。  
  
    -   上のグリッドで 1 つ以上の行を選択し、 **[削除]** をクリックする。これは、データに変更を加えずに **[優先されたデータの送信]** をクリックするのと同じです。  
  
    -   プロパティボタン ([.**..**]) をクリックして、競合に関係する列の詳細情報を表示します。  
  
    -   データを送信する前に、 **[競合で優先されたデータ]** 列または **[競合で優先されなかったデータ]** 列でデータを編集する (列が灰色の場合、データは読み取り専用です)。  
  
    -   **[優先されたデータの送信]** をクリックし、競合で優先するデータとして指定された行を受け入れる。  
  
    -   **[優先されなかったデータの送信]** をクリックして解決をオーバーライドし、競合で優先されないデータとして指定された値をトポロジのすべてのノードに反映する。  
  
    -   **[この競合の詳細をログに記録する]** を選択して、競合のデータをログ ファイルに記録する。 ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。 値を入力するか、または参照ボタン (**[...]**) をクリックして適切なファイルに移動します。 **[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを終了します。  
  
6.  レプリケーション競合表示モジュールを閉じます。  
  
## <a name="see-also"></a>参照  
 [マージレプリケーションの競合検出と解決の詳細](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [マージ アーティクル競合回避モジュールの指定](publish/specify-a-merge-article-resolver.md)  
  
  
