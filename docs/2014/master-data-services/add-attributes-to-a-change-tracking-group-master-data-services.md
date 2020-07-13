---
title: 変更の追跡グループに属性を追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e4457412f39b6dbaa86154dc6068527d7b2095d3
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972325"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>変更の追跡グループに属性を追加する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で属性の値に対する変更を追跡する場合、変更の追跡グループに属性を追加します。  
  
> [!NOTE]  
>  変更の追跡グループに属性を追加した後に属性の値が変更されると、属性は [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで変更済みとしてフラグが付けられます。 変更に基づいてアクションを実行するビジネス ルールを作成します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   変更の追跡グループに追加する属性が存在する必要があります。 詳細については、「 [テキスト属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)」を参照してください。  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>属性を変更の追跡グループに追加するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  [**モデルエクスプローラー** ] ページのメニューバーから [**管理**] をポイントし、[**エンティティ**] をクリックします。  
  
3.  **[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  属性値を追跡するエンティティの行を選択します。  
  
5.  **[選択したエンティティの編集]** をクリックします。  
  
6.  **[エンティティの編集]** ページで、次の手順を実行します。  
  
    -   リーフメンバーの属性の場合は、[**リーフ属性**] ペインで属性を選択し、[**リーフ属性の編集**] をクリックします。  
  
    -   統合メンバーの属性の場合は、[**統合属性**] ペインで属性を選択し、[**統合属性の編集**] をクリックします。  
  
    -   コレクションの属性の場合は、[**コレクション属性**] ペインで属性を選択し、[**コレクション属性の編集**] をクリックします。  
  
7.  **[変更の追跡の有効化]** チェック ボックスをオンにします。  
  
8.  **[変更の追跡グループ]** ボックスにグループの番号を入力します。  
  
9. **[属性の保存]** をクリックします。  
  
10. **[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。  
  
11. グループに含めるすべての属性に対して、この手順を繰り返します。 グループ内の各属性に対して同じ変更の追跡グループの番号を使用します。  
  
## <a name="next-steps"></a>次の手順  
  
-   [属性値の変更に基づいてアクションを開始する (マスター データ サービス)](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [テキスト属性 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [ドメイン ベースの属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
