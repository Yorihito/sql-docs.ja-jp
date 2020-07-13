---
title: Cube ストレージ (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- measure groups [Analysis Services], cubes
- cubes [Analysis Services], storage
- linked measure groups [Analysis Services]
- storing data [Analysis Services], cubes
- partitions [Analysis Services], cubes
- storage [Analysis Services], cubes
ms.assetid: 1b1ad360-9a9b-4996-bee9-84238a2bb4ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: eef1dd188b0038c637dc15750a6538c929359299
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545292"
---
# <a name="cube-storage-analysis-services---multidimensional-data"></a>キューブのストレージ (Analysis Services - 多次元データ)
  ストレージには、キューブのメタデータのみが含まれている場合も、ファクト テーブルのすべてのソース データだけでなく、メジャー グループに関連付けられたディメンションによって定義されている集計も含まれている場合もあります。 格納されているデータ量は、選択したストレージ モードおよび集計の数によって異なります。 格納されているデータの量は、クエリのパフォーマンスに直接影響を与えます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、キューブデータおよび集計の格納に必要な領域を最小限に抑えるために、いくつかの手法が使用されています。  
  
-   ストレージ オプションを使用すると、キューブ データに最適なストレージ モードとストレージの場所を選択できる。  
  
-   洗練されたアルゴリズムによって効率的に要約を行い、速度を維持してストレージ領域を最小限に抑える。  
  
-   空のセルにはストレージ領域を割り当てない。  
  
 ストレージは、パーティションごとに定義され、キューブ内の各メジャー グループに対して少なくとも 1 つのパーティションが存在します。 詳細については、「[パーティション &#40;Analysis Services 多次元データ&#41;](partitions-analysis-services-multidimensional-data.md)」、「[パーティションストレージモードと処理](partitions-partition-storage-modes-and-processing.md)」、「[メジャーとメジャーグループ](../multidimensional-models/measures-and-measure-groups.md)」、および「[多次元モデルでのメジャーとメジャーグループの作成](../multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)」を参照してください。  
  
## <a name="partition-storage"></a>パーティション ストレージ  
 メジャー グループのストレージは、複数のパーティションに分割できます。 パーティションに分割すると、メジャー グループを 1 台のサーバー上または複数のサーバーにまたがる個別のセグメントに分散し、ストレージやクエリのパフォーマンスを最適化できます。 メジャー グループ内の各パーティションは、異なるデータ ソースを基にして、異なるストレージ設定を使用して格納できます。  
  
 パーティションのデータ ソースは作成時に指定します。 また、既存のパーティションのデータ ソースを変更することもできます。 メジャー グループは、列方向または行方向にパーティション分割できます。 列方向にパーティション分割されたメジャー グループの各パーティションは、1 つのソース テーブルのフィルターされたビューに基づいています。 たとえば、メジャー グループが数年間のデータを含んでいる 1 つのテーブルに基づいている場合、各年のデータごとに個別のパーティションを作成できます。 一方、行方向にパーティション分割されたメジャー グループの各パーティションは、個別のテーブルに基づいています。 データ ソースが個別のテーブルに各年のデータを格納している場合は、行方向のパーティション分割を使用します。  
  
 パーティションは最初、パーティションが作成されるメジャー グループと同じストレージ設定で作成されます。 ストレージ設定により、詳細および集計データを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに多次元形式で格納するか、またはソース サーバーにリレーショナル形式で格納するか、あるいはその両方の組み合わせで格納するかが決まります。 また、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に格納されている多次元データへのソース データ変更について、プロアクティブ キャッシュを使用して自動的に処理するかどうかも、ストレージ設定によって決まります。  
  
 キューブのパーティションは、ユーザーからは見えません。 ただし、各種パーティションに対するストレージ設定の選択内容は、データの即時性、使用されるディスク領域の量、およびクエリのパフォーマンスに影響を及ぼすことがあります。 パーティションは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の複数のインスタンスに格納できます。 これにより、キューブ ストレージをクラスター化して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー間でワークロードを分散できます。 詳細については、「[パーティションストレージモードと処理](partitions-partition-storage-modes-and-processing.md)、[リモートパーティション](partitions-remote-partitions.md)、および[パーティション &#40;Analysis Services-多次元データ&#41;](partitions-analysis-services-multidimensional-data.md)」を参照してください。  
  
## <a name="linked-measure-groups"></a>リンク メジャー グループ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の異なるインスタンスにキューブの複数のコピーを格納するために非常に大きなディスク領域が必要になる場合がありますが、メジャー グループのコピーをリンク メジャー グループに置き換えることで、必要な領域を大幅に削減できます。 リンク メジャー グループは、同じまたは異なる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス上の別の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内にあるキューブのメジャー グループに基づいています。 リンク メジャー グループは、同じソース キューブのリンク ディメンションと共に使用することもできます。 リンク ディメンションとリンク メジャー グループでは、ソース キューブの集計が使用され、独自のデータのストレージ容量はありません。 このため、1 つのデータベースで基になるメジャー グループとディメンションを維持し、他のデータベースのキューブでリンク キューブとリンク ディメンションを作成すると、ストレージとして使用されるディスク領域を節約できます。 詳細については、「[リンクメジャーグループ](../multidimensional-models/linked-measure-groups.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [集計と集計デザイン](aggregations-and-aggregation-designs.md)  
  
  
