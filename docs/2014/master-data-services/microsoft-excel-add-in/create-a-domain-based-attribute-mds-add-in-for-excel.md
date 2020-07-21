---
title: ドメイン ベースの属性の作成 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 93a22979296e397ebe9c28a014913ca9da592ee6
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961322"
---
# <a name="create-a-domain-based-attribute-mds-add-in-for-excel"></a>ドメイン ベースの属性の作成 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の管理者は、列内の値を特定の一連の値に制約する場合に、ドメイン ベースの属性を作成できます。  
  
 使用できるのは、既にワークシート内にある値か、既存のエンティティの値です。  
  
> [!NOTE]  
>  制約された列の値を、一覧から選択せずにユーザーが入力すると、パブリッシュ時に **[$InputStatus$]** 列にエラーが表示されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** および **[エクスプローラー]** 機能領域に対する権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](../administrators-master-data-services.md)」を参照してください。  
  
-   モデルとエンティティが既に存在している必要があります。  
  
### <a name="to-perform-this-procedure"></a>この手順を実行するには  
  
1.  Excel で、制約する列 (属性) を含むエンティティを読み込みます。 詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。  
  
2.  制約する列の任意のセルをクリックします。  
  
3.  **[モデルの構築]** グループの **[属性プロパティ]** をクリックします。  
  
4.  **[属性プロパティ]** ダイアログ ボックスで、 **[属性の型]** ボックスの一覧の **[制約付き一覧 (ドメイン ベース)]** をクリックします。  
  
5.  **[属性に次の値を設定]** ボックスの一覧で、次の操作を実行します。  
  
    -   ワークシートの値を使用するには、[ **選択した列**] をクリックします。 選択した列の値を使用して、新しいエンティティと新しいステージング テーブルが作成されます。  
  
    -   既存のエンティティの値を使用するには、エンティティの名前を選択します。  
  
6.  前の手順で **[選択した列]** をクリックした場合は、 **[新しいエンティティ名]** ボックスに新しいエンティティの名前を入力します。 列 (属性) と同じ名前にすることができます。  
  
7.  **[OK]** をクリックします。 これで、列内の各セルに、ユーザーが選択する値の一覧が設定されます。  
  
## <a name="next-steps"></a>次の手順  
  
-   制約された一覧の値を追加および削除するには、その属性が基づいているエンティティを読み込みます。 エンティティの読み込みの詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ドメインベースの属性 &#40;マスターデータサービス&#41;](../domain-based-attributes-master-data-services.md)   
 [エンティティ &#40;Excel 用 MDS アドインを作成し&#41;](create-an-entity-mds-add-in-for-excel.md)   
 [モデルの構築 (Excel 用 MDS アドイン)](building-a-model-mds-add-in-for-excel.md)  
  
  
