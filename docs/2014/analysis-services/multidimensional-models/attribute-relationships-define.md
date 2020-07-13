---
title: 属性リレーションシップの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
ms.openlocfilehash: d75bf3ec0aa6e7199b1e6f8d31e2602deb8efeff
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544674"
---
# <a name="define-attribute-relationships"></a>属性リレーションシップの定義
  で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、属性はディメンションの基本的な構成要素です。 ディメンションには、属性リレーションシップに基づいて構成される一連の属性が含まれます。  
  
 ディメンションに含まれるテーブルごとに、テーブルのキー属性をそのテーブルの別の属性に関連付ける属性リレーションシップがあります。 このリレーションシップは、ディメンションの作成時に作成します。  
  
 属性リレーションシップには、次の利点があります。  
  
-   ディメンション処理に必要なメモリの量が減少します。 これにより、ディメンション、パーティション、およびクエリの処理速度が上がります。  
  
-   ストレージへのアクセスが高速になり、実行プランがより適切に最適化されるため、クエリ パフォーマンスが向上します。  
  
-   ユーザー定義階層がリレーションシップのパスに沿って定義されている場合、集計デザイン アルゴリズムによってより効果的な集計が選択されます。  
  
    > [!NOTE]  
    >  属性リレーションシップの定義と構成の重要性および影響の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンスガイド](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)」の「クエリパフォーマンスの向上」を参照してください。  
  
## <a name="attribute-relationship-considerations"></a>属性リレーションシップに関する注意点  
 基になるデータで属性リレーションシップがサポートされる場合、属性間で一意の属性リレーションシップを定義することも必要です。 一意の属性リレーションシップを定義するには、ディメンション デザイナーの **[属性リレーションシップ]** タブを使用します。  
  
 基になるリレーションシップがある属性には、その関連属性を基準とした一意なキーが必要です。 つまり、基になる属性のメンバーによって、関連属性のメンバーが 1 つだけ識別される必要があります。 たとえば、市区町村 -> 都道府県のリレーションシップを考えてみます。 このリレーションシップでは、基になる属性が市区町村、関連属性が都道府県です。 Source 属性は "many" 側で、関連側は多対一リレーションシップの "一" 側です。 基になる属性のキーは、市区町村 + 都道府県です。 詳細については、「 [属性リレーションシップの作成、変更、または削除](attribute-relationships-create-modify-or-delete-relationship.md)」を参照してください。  
  
 属性リレーションシップのプロパティの詳細については、「 [属性リレーションシップのプロパティの構成](attribute-relationships-configure-attribute-properties.md)」を参照してください。  
  
> [!NOTE]  
>  属性リレーションシップを正しく定義しないと、クエリ結果が無効になる場合があります。  
  
## <a name="see-also"></a>参照  
 [のディメンション デザイナーでは、[ディメンション構造] ビューの](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
