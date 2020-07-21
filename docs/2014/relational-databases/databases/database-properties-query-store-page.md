---
title: '[データベースのプロパティ] ([クエリ ストア] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.querystore.f1
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
author: stevestein
ms.author: sstein
ms.openlocfilehash: bab0d9b697e9ad9ec4b27f320d26b9b9edb5944e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970122"
---
# <a name="database-properties-query-store-page"></a>データベースのプロパティ (クエリのストアのページ)
  このページにはプリンシパル データベースからアクセスし、これを使用してデータベースのクエリのストアのプロパティを構成および変更します。 これらのオプションは、 [ALTER DATABASE SET オプション](/sql/t-sql/statements/alter-database-transact-sql-set-options)を使用して構成することもできます。 クエリのストアの詳細については、「 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)」をご覧ください。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]|  
  
## <a name="options"></a>オプション  
 有効にする  
 クエリのストアを有効化または無効化します。  
  
 操作モード  
 有効な値は、READ_ONLY、READ_WRITE はします。 READ_WRITE モードでは、クエリのストアでクエリ プランとランタイム実行の統計情報が収集および保持されます。 READ_ONLY モードでは、クエリのストアから情報を読み取ることができますが、新しい情報は追加されません。 クエリのストアの割り当て済み最大領域が不足すると、クエリのストアは操作モードを READ_ONLY にします。  
  
 操作モード (実際)  
 クエリのストアの実際の操作モードを取得します。  
  
 操作モード (要求)  
 クエリのストアの目的の操作モードを取得、および設定します。  
  
 データ フラッシュ間隔 (分)  
 クエリ ストアに書き込まれるデータがディスクに永続化される頻度を決定します。 パフォーマンスを最適化するため、クエリ ストアで収集したデータは非同期的にディスクに書き込まれます。 この非同期転送が発生する頻度が構成されます。  
  
 統計情報の収集間隔  
 統計情報の収集間隔を取得、および設定します。  
  
 最大サイズ (MB)  
 クエリのストアに割り当てられた合計領域を取得、および設定します。  
  
 古いクエリのしきい値 (日)  
 古いクエリのしきい値を取得、および設定します。 STALE_QUERY_THRESHOLD_DAYS 引数を構成して、クエリのストア内にデータを保持する日数を指定します。  
  
 クエリ データの消去  
 クエリ ストアの内容を削除します。  
  
 円グラフ  
 左側のグラフには、ディスク上のデータベース ファイルの合計消費量、およびクエリのストアのデータを格納するファイルの部分が表示されます。  
  
 右側のグラフには、現在使用されているクエリのストアのクォータの部分が表示されます。 クォータは、左側のグラフには表示されないことにご注意ください。 クォータが、データベースの現在のサイズを超える場合があります。  
  
## <a name="remarks"></a>注釈  
 クエリのストアの機能により、クエリ プランの選択やパフォーマンスに関する洞察が DBA に提供されます。 これにより、クエリ プランの変更によって生じるパフォーマンスの違いがすばやくわかるようになり、パフォーマンス上のトラブルシューティングを簡略化できます。 この機能により、クエリ、プラン、ランタイム統計情報の履歴が自動的にキャプチャされ、レビュー用に保持されます。 データは時間枠で区分されるため、データベースの使用パターンを表示して、サーバー上でクエリ プランが変わった時点を確認することができます。 クエリのストアは、クエリのストアのデータベース プロパティ ページを使用するか、 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) オプションを使用して構成できます。 クエリのストアは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ダイアログ ボックスを使用して情報を表示します。 クエリのストアの詳細については、「 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャのクエリストア](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql)   
 [クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/query-store-catalog-views-transact-sql)  
  
  
