---
title: ワークロード グループの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f73b48f0ec2255760b4ee55acfaf91dc02af7cd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063563"
---
# <a name="move-a-workload-group"></a>ワークロード グループの移動
  リソース ガバナーのワークロード グループを別のリソース プールに移動するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。  
  
-   **作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)  
  
-   **ワークロード グループの移動に使用するもの:** [SQL Server Management Studio](#MoveWGSSMS)、[Transact-SQL](#MoveWGTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
 リソース ガバナーの保留中の構成操作がある場合、ワークロード グループを移動できません。  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 リソース ガバナーの保留中の構成操作がある場合、ワークロード グループを移動できません。 [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 動的管理ビューにクエリを実行して is_configuration_pending の現在の状態を取得することにより、構成が保留中かどうかを確認できます。  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 ワークロード グループを移動するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="move-a-workload-group-using-sql-server-management-studio"></a><a name="MoveWGSSMS"></a> SQL Server Management Studio を使用してワークロード グループを移動する  
 **を使用してワークロード グループを移動するには [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**  
  
1.  オブジェクト エクスプローラーで、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。  
  
2.  **[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックすると、 **[リソース ガバナーのプロパティ]** ページが開きます。  
  
3.  **[リソース プール]** ウィンドウで、移動するワークロード グループを含むリソース プールをクリックします。 **[ワークロード グループ]** ウィンドウに、対象リソース プール内のワークロード グループが表示されます。  
  
4.  **[ワークロード グループ]** ウィンドウで、移動するワークロード グループの左にある右矢印を右クリックして **[移動先]** をクリックします。 **[ワークロード グループの移動]** ウィンドウが表示されます。  
  
5.  使用可能なリソース プールがウィンドウに表示されます。 ワークロード グループの移動先とするリソース プールの名前をクリックし、 **[OK]** をクリックしてこの操作を実行します。  
  
6.  この操作は、 **[OK]** をクリックするまで完了しません。 **[OK]** をクリックすると、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントが実行されます。  
  
7.  リソース プールまたはワークロード グループの作成操作または再構成操作が失敗した場合は、プロパティ ページのタイトルの下に簡単なエラー メッセージが表示されます。 詳細なエラー メッセージを表示するには、エラー メッセージの下矢印をクリックします。  
  
##  <a name="move-a-workload-group-using-transact-sql"></a><a name="MoveWGTSQL"></a> Transact-SQL を使用してワークロード グループを移動する  
 **Transact-SQL を使用してワークロード グループを移動するには**  
  
1.  移動するワークロード グループと移動先とするリソース プールの名前を指定する `ALTER WORKLOAD GROUP` ステートメントを実行します。  
  
2.  **ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。  
  
### <a name="example-transact-sql"></a>例 (Transact-SQL)  
 次の例では、 `groupAdhoc` という名前のワークロード グループを既定のリソース プールに移動します。  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [リソース ガバナー](resource-governor.md)   
 [リソース ガバナーの有効化](enable-resource-governor.md)   
 [リソース プールの作成](create-a-resource-pool.md)   
 [ワークロード グループの作成](create-a-workload-group.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
