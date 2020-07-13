---
title: ビジネス ルールを作成しパブリッシュする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 78fca612d75d0436e0d47870b715d5d810937c71
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971700"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a>ビジネス ルールを作成しパブリッシュする (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、マスター データの精度を保証するためにビジネス ルールを作成します。 ルールを作成した後、データに適用する前に、そのルールをパブリッシュする必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-create-and-publish-a-business-rule"></a>ビジネス ルールを作成してパブリッシュするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  **[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  **[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。  
  
6.  **[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。  
  
7.  **[ビジネス ルールの追加]** をクリックします。  
  
8.  **[選択したビジネス ルールの編集]** をクリックします。  
  
9. **[コンポーネント]** ペインで **[条件]** ノードを展開します。  
  
10. 条件をクリックし、[ **IF** ] ペインの [**条件**] ラベルにドラッグします。  
  
    > [!TIP]  
    >  ビジネスルールからアイテムを削除するには、右クリックして [**削除**] を選択します。  
  
11. [**属性**] ペインで属性をクリックし、[条件の**編集**] ペインの **[属性の選択]** ラベルにドラッグします。  
  
12. [**条件の編集**] ウィンドウで、必要なフィールドを入力します。  
  
13. **[条件の編集]** ペインの **[アイテムの保存]** をクリックします。  
  
14. **[コンポーネント]** ペインで **[アクション]** ノードを展開します。  
  
15. アクションをクリックして、 **[THEN]** ペインの **[アクション]** ラベルにドラッグします。  
  
16. **[属性]** ペインで属性をクリックして、 **[アクションの編集]** ペインの **[属性の選択]** ラベルにドラッグします。  
  
17. **[アクションの編集]** ペインで、必須の各フィールドを入力します。  
  
18. **[アクションの編集]** ペインの **[アイテムの保存]** をクリックします。  
  
19. オプションで、ビジネス ルールに複数の条件を追加します。 詳細については、「 [ビジネス ルールに複数の条件を追加する (マスター データ サービス)](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)」を参照してください。  
  
20. **[戻る]** をクリックします。  
  
21. 必要に応じて、 **[ビジネス ルールのメンテナンス]** ページで、ビジネス ルールを含む行の **[名前]**、 **[説明]**、または **[通知]** 列のセルをダブルクリックして値を更新します。  
  
    > [!NOTE]  
    >  通知は、検証アクションを含むルールに対してのみ送信されます。  
  
22. **[ビジネス ルールのパブリッシュ]** をクリックします。  
  
23. 確認のダイアログ ボックスで **[OK]** をクリックします。 ルールの状態が **[アクティブ]** に変わります。  
  
## <a name="next-steps"></a>次の手順  
  
-   以下のいずれかの手順でビジネス ルールをデータに適用します。  
  
    -   [ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [通知を送信するようにビジネスルールを構成する &#40;マスターデータサービス&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)   
 [ビジネスルールの名前を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [ビジネス ルールに複数の条件を追加する &#40;マスター データ サービス&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
