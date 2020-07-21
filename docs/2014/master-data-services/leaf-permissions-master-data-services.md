---
title: リーフ アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf091886adb0a7fe484b2b62f44eb51b6c58d8bc
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971272"
---
# <a name="leaf-permissions-master-data-services"></a>リーフ権限 (Master Data Services)
  リーフ権限は、エンティティのすべてのリーフ メンバーの属性値に適用されます。  
  
 明示的階層が有効になっていないエンティティの場合、 **リーフ** への権限の割り当ては、エンティティへの権限の割り当てと同じです。  
  
 **注:**  
  
-   リーフ権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
-   **Name** 属性および **Code** 属性に割り当てられる権限は適用されません。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用**|リーフ メンバーが表示されますが、ユーザーはそれらのメンバーを追加、削除、または変更できません。<br /><br /> 統合メンバーが存在する場合は、名前とコードが表示されますが、ユーザーはそれらを追加、削除、または変更できません。|  
|**Update**|リーフ メンバーが表示され、ユーザーはそれらのメンバーを追加、削除、および変更できます。<br /><br /> 統合メンバーが存在する場合は、名前とコードが表示されますが、ユーザーはそれらを追加、削除、または変更できません。|  
|**Deny**|エンティティのリーフ メンバーが表示されません。|  
  
## <a name="attribute-permissions"></a>属性の権限  
 属性の権限は、特定のエンティティの属性の値に適用されます。 属性の権限のみを持つユーザーは、メンバーを追加または削除できません。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用**|属性が表示されますが、ユーザーは属性の値を変更できません。|  
|**Update**|属性が表示され、ユーザーは属性の値を変更できます。|  
|**Deny**|属性が表示されません。<br /><br /> 注: Name 属性と Code 属性へのアクセスを明示的に拒否することはできません。|  
  
### <a name="example"></a>例  
 Product エンティティの場合、Subcategory 属性に **更新** 権限を割り当てます。 他のすべての属性に対しては権限を拒否します。  
  
|名前|コード|Subcategory (更新)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5}マウンテンバイク|  
|Mountain-100|BK-M201|{5}マウンテンバイク|  
  
 **[エクスプローラー]** では、Subcategory 列の属性値を更新できます。 属性に対する権限がない場合、その属性は表示されません。  
  
> [!NOTE]  
>  この例では、Subcategory は、SubcategoryList エンティティに基づくドメイン ベースの属性です。 Mountain-100 に対して別のサブカテゴリを選択することはできますが、SubcategoryList エンティティへのメンバーの追加または SubcategoryList エンティティからのメンバーの削除を行うことはできません。  
  
## <a name="see-also"></a>参照  
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](assign-model-object-permissions-master-data-services.md)   
 [統合アクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [属性 (マスター データ サービス)](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
