---
title: オブジェクトカウントの指定 (集計のデザインウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 305d9d79-d1ab-4704-a7b5-3283842b3996
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66b972395f86746b2d08df234db8aa0c71d03fd
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940323"
---
# <a name="specify-object-counts-aggregation-design-wizard"></a>[オブジェクト カウントの指定] (集計のデザイン ウィザード)
  **[オブジェクト カウントの指定]** ページを使用すると、キューブ内のオブジェクト数を自動的に計算したり、推定カウントを手動で入力したりできます。 集計のデザイン ウィザードでは、オブジェクト カウントを使用してストレージ要件を推定します。  
  
## <a name="options"></a>オプション  
 **[キューブ オブジェクト]**  
 キューブ内のディメンションおよび属性を表示します。 `AggregationUsage` `None` カウントを指定する必要がある唯一の属性であるため、ウィザードの [**集計使用法の確認**] ページでプロパティがに設定されていない属性のみが表示されます。  
  
 **[推定カウント]**  
 メジャー グループ内の推定行数およびデータベース ディメンション内の属性の推定メンバー数を表示します。 推定カウントとして使用する値を入力することも、推定カウントの値を計算することもできます。 カウント値を計算するには、フィールドに「」と入力し、 `0` [**カウント**] をクリックします。 既にカウントが表示されているフィールドは更新されません。  
  
 **パーティション数**  
 (省略可) メジャー グループ内の推定行数およびパーティション内の属性の推定メンバー数を入力します。  
  
 **Count**  
 空のすべてのフィールドに対する **[推定カウント]** 列の値を計算し、再作成します。 既にカウントが表示されているフィールドは更新されません。  
  
## <a name="see-also"></a>参照  
 [集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード &#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
