---
title: 既存のデータベースを複製する
description: データベースを複製する方法について説明します。 新しいデータベースの作成、そのスキーマの複製とそのデータのレプリケートに関連する手順を確認します。
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: aad3594a-11cf-4e68-a622-071a93d43875
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 03dedf5c30c8370195243c11406552d12edd8394
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2020
ms.locfileid: "85518902"
---
# <a name="how-to-clone-an-existing-database"></a>方法:既存のデータベースを複製する

このタスクでは、これまでに学んだいくつかの手順を利用して、新しいデータベースを作成し、既存のデータを移行します。 また、「[スキーマ比較を使用して各種のデータベース定義を比較する方法](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)」に示されている手順を使用して、ソースのスキーマとプロジェクト データベースを同期します。  
  
これらの手順を使用すると、運用データベースから、同じスキーマおよびデータを持つ開発用またはテスト用のデータベースを容易に作成できます。 運用データベースの使用を妨害することなく、テスト用データベースの開発を接続モードで続行することも、オフラインの開発用およびテスト用にデータベース プロジェクトを作成することもできます。  
  
> [!WARNING]  
> 以下に示す手順では、「[接続されているデータベース開発](../ssdt/connected-database-development.md)」に示されているこれまでの手順で作成したエンティティを使用します。  
  
### <a name="to-create-a-development-database"></a>開発用データベースを作成するには  
  
1.  **SQL Server オブジェクト エクスプローラー**の **[SQL Server]** ノードの下で、接続されているサーバー インスタンスを展開します。  
  
2.  **[データベース]** ノードを右クリックし、 **[新しいデータベースの追加]** をクリックします。  
  
3.  新しいデータベースの名前を **TradeDev** に変更します。  
  
4.  **SQL Server オブジェクト エクスプローラー**で **Trade** データベースを右クリックし、 **[スキーマ比較]** をクリックします。 元の **Trade** データベースをソースとして、新しい **TradeDev** データベースをターゲットとして選択し、「[スキーマ比較を使用して各種のデータベース定義を比較する方法](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)」の手順に従います。 これにより、**TradeDev** が **Trade** のスキーマで更新されます。  
  
### <a name="to-replicate-data"></a>データをレプリケートするには  
  
1.  前の手順では、運用データベースのスキーマのみが、開発用データベースに複製されました。 この手順では、運用データを開発用データベースに複製します。  
  
    **Trade** データベースの **Suppliers** テーブルを右クリックし、 **[データの表示]** をクリックします。 データ エディターが開きます。  
  
2.  ツール バーの **[最大行数]** の横にある **[スクリプト]** をクリックします。  
  
3.  スクリプト ウィンドウが開いたら、Transact\-SQL スクリプト ペインの下のステータス バーに、"接続しました" と表示されることを確認します。 "接続解除されました" と表示された場合は、 **[接続]** (ツール バーの左端のボタン) をクリックし、サーバー情報および資格情報を入力します。  
  
4.  **[接続]** / **[切断]** の横にある **[データベース]** ボックスの一覧で、**TradeDev** をクリックします。 これは Transact\-SQL`USE` ステートメントと似ており、コード エディター内のスクリプトを **TradeDev** データベースに対して実行することが指定されます。  
  
5.  **[クエリの実行]** をクリックして、`INSERT` ステートメントを実行します。 これにより、`Suppliers` データベースの `Trade` テーブルの行がすべて、`Suppliers` データベースの `TradeDev` テーブルに挿入されます。  
  
6.  `Trade` データベースのすべてのテーブルについて、これまでの手順を繰り返すことにより、これらを `TradeDev` データベースにレプリケートします。  
  
7.  データ エディターを使用して、新しい `TradeDev` データベースのすべてのテーブルにデータが設定されていることを確認します。  
  
## <a name="see-also"></a>参照  
[方法:  スキーマ比較を使用して各種のデータベース定義を比較する](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
