---
title: データソースビューでのスキーマの更新 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services], schema updates
- refreshing data source views
- data source views [Analysis Services], refreshing
ms.assetid: 634b0504-1437-43e7-8ac7-3248ac7989a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5427978b2ef09238763efb5f50dd579456e99244
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545784"
---
# <a name="refresh-the-schema-in-a-data-source-view-analysis-services"></a>データ ソース ビューでのスキーマの更新 (Analysis Services)
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベースでデータ ソース ビュー (DSV) を定義した後に、基になるデータ ソースのスキーマが変更される場合があります。 開発プロジェクトでは、これらの変更は自動的に検出または更新されません。 さらに、プロジェクトをサーバーに配置した場合に、Analysis Services が外部データ ソースに接続できないという処理エラーが発生します。

 外部データ ソースと一致するように DSV を更新するには、Business Intelligence Development Studio (BIDS) で DSV を更新します。 DSV を更新すると、DSV の基になる外部データ ソースへの変更が検出され、外部データ ソース内の追加と削除を列挙した変更リストが構築されます。 その後、再配置を行う DSV への一連の変更を、基になるデータ ソースに適用できます。 DSV を使用するプロジェクトでキューブとディメンションをさらに更新するために、追加の作業が必要になることがよくあります。

 このトピックのセクションは次のとおりです。

 [更新でサポートされている変更](#bkmk_changlist)

 [SQL Server Data Tools での DSV の更新](#bkmk_DSVrefresh)

##  <a name="changes-supported-in-refresh"></a><a name="bkmk_changlist"></a>更新でサポートされている変更
 DSV 更新には、次のアクションを含めることができます。

-   テーブル、列、およびリレーションシップの削除。

-   列およびリレーションシップの追加 (DSV に既に含まれているテーブルに適用)。

-   新しい一意の制約の追加。 DSV のテーブルに論理主キーが存在し、データ ソースのテーブルに物理キーが追加されると、論理キーが削除され、物理キーで置換されます。

 更新によって DSV に新しいテーブルが追加されることはありません。 新しいテーブルを追加する場合は、手動で追加する必要があります。 詳細については、「 [データ ソース ビューでのテーブルまたはビューの追加または削除 (Analysis Services)](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)内のソリューション エクスプローラーでデータ ソース ビュー ウィザードを実行します。

##  <a name="refresh-a-dsv-in-sql-server-data-tools"></a><a name="bkmk_DSVrefresh"></a>SQL Server Data Tools で DSV を更新する
 DSV を更新するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで [DSV] をダブルクリックしてから、[データ ソース ビューを最新状態に更新] をクリックするか、[データ ソース ビュー] メニューの **[更新]** をクリックします。

 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、更新中、基になるリレーショナル データ ソースのすべてにクエリして、DSV に含まれているテーブルやビューが変更されたかどうかを調べます。 基になるデータ ソースのすべてに接続を確立できる場合は、変更されていれば **[データ ソース ビューを最新状態に更新]** ダイアログ ボックスに表示されます。

 ![[データソースビューの更新] ダイアログボックス](../media/ssas-olapdsv-refresh.gif "[データ ソース ビューを最新状態に更新] ダイアログ ボックス")

 ダイアログ ボックスには、DSV で削除または追加されるテーブル、列、制約、およびリレーションシップが一覧表示されます。 また、レポートには、正常に準備できない名前付きクエリまたは計算も一覧表示されます。 影響を受けたオブジェクトは、テーブルで入れ子になった列およびリレーションシップと、オブジェクトごとに示されている変更の種類 (削除または追加) と共に、ツリー ビューに一覧表示されます。 標準的なデータ ソース ビューのオブジェクト アイコンは、影響を受けたオブジェクトの種類を示します。

 更新は、基になるオブジェクトの名前に完全に基づいています。 そのため、基になるオブジェクトの名前がデータソースで変更された場合、データソースビューデザイナーは、名前が変更されたオブジェクトを、削除と加算という2つの別個の操作として扱います。 この場合、名前が変更されたオブジェクトをデータ ソース ビューに手動で追加し直すことが必要な場合があります。 また、リレーションシップまたは論理主キーを再作成することが必要な場合もあります。

> [!IMPORTANT]
>  データ ソースでテーブルの名前が変更されたことがわかっている場合は、 **[テーブルの置換]** コマンドを使用して、データ ソース ビューを更新する前に、テーブルを名前変更後のテーブルで置換することが必要な場合があります。 詳細については、「[データ ソース ビュー内のテーブルまたは名前付きクエリの置換 (Analysis Services)](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)」をご覧ください。

 レポートの確認後は、変更内容を受け入れるか、更新を取り消して変更内容を拒否することができます。 すべての変更はまとめて受け入れるか拒否する必要があります。 一覧の個々のアイテムを選択することはできません。 また、変更内容のレポートを保存することもできます。

## <a name="see-also"></a>参照
 [多次元モデル内のデータ ソース ビュー](data-source-views-in-multidimensional-models.md)


