---
title: モデル オブジェクト アクセス許可を割り当てる (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7924ef8effaa3c39802fd53216814b065ff81ef4
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972212"
---
# <a name="assign-model-object-permissions-master-data-services"></a>モデル オブジェクト権限を割り当てる (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、 **の** [エクスプローラー] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域内のデータにユーザーまたはグループがアクセスできるようにする必要があるとき、またはユーザーまたはグループを管理者にする必要があるときは、モデル オブジェクトに権限を割り当てます。  
  
> [!NOTE]  
>  モデルに権限を割り当てると、その他のすべてのモデルへの権限は暗黙的に拒否されます。 モデル オブジェクト権限を割り当てない場合、ユーザーまたはグループは **[エクスプローラー]** のデータにアクセスできません。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-assign-model-object-permissions"></a>モデル オブジェクト権限を割り当てるには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。  
  
2.  **[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。  
  
3.  **[選択したユーザーの編集]** をクリックします。  
  
4.  **[モデル]** タブをクリックします。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します (オプション)。  
  
6.  **[編集]** をクリックします。  
  
7.  ツリーを展開して、権限を割り当てるモデル オブジェクトをクリックします。  
  
8.  メニューから、[**読み取り**専用]、[**更新**]、または [**拒否**] を選択します。  
  
9. **[保存]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   (省略可能) [階層メンバーの権限を割り当てる (マスター データ サービス)](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [マスターデータサービス&#41;&#40;モデルオブジェクト権限の削除](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [モデル管理者を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
