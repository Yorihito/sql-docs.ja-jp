---
title: フルテキスト インデックスの作成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], about
ms.assetid: f8a98486-5438-44a8-b454-9e6ecbc74f83
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 603b5e6b929259dc8b1408c0c2a1afab383446e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055519"
---
# <a name="create-and-manage-full-text-indexes"></a>フルテキスト インデックスの作成と管理
  フルテキスト インデックスの情報は、特定の単語や単語の組み合わせをすばやく検索できるフルテキスト クエリをコンパイルするために Full-Text Engine で使用されます。 フルテキスト インデックスには、データベース テーブルの 1 つ以上の列の重要な語およびその場所に関する情報が保存されます。 フルテキスト インデックスは、Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]により構築および管理されるトークンベースの特殊な機能インデックスです。 フルテキスト インデックスの作成手順は、他のタイプのインデックスの作成手順とは異なります。 特定の行に格納された値に基づいて B ツリー構造を作成するのではなく、Full-Text Engine は、インデックスを作成するテキストの個々のトークンに基づいて、反転、スタック、および圧縮されたインデックス構造を作成します。  フルテキスト インデックスのサイズを制限する要因となるのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが実行されているコンピューターで使用できるメモリ リソースのみです。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、フルテキスト インデックスはデータベース エンジンと統合されており、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のようにファイル システムには格納されません。 新しいデータベースでは、フルテキスト カタログは、ファイル グループに属さない仮想オブジェクトです。これは、フルテキスト インデックスのグループを指す論理的概念に過ぎません。 ただし、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースをアップグレードする場合は、データ ファイルを含むフルテキスト カタログの新しいファイル グループが作成されます。詳細については、「 [フルテキスト検索のアップグレード](upgrade-full-text-search.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、Full-Text Engine は、個別のサービスではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス内に存在します。 Full-Text Engine をデータベース エンジンに統合することにより、フルテキストの管理、混合クエリの最適化、および全体的なパフォーマンスが向上しています。  
  
 1 つのテーブルに対し、1 つのフルテキスト インデックスしか使用できません。 フルテキスト インデックスをテーブルに作成するためには、一意で NULL が許容されない列がそのテーブルに 1 つ必要です。 フルテキスト インデックスを作成できるのは、データ型が `char`、`varchar`、`nchar`、`nvarchar`、`text`、`ntext`、`image`、`xml`、`varbinary`、および `varbinary(max)` の列です。これらの列には、フルテキスト検索用のインデックスを作成できます。 データ型が `varbinary`、`varbinary(max)`、`image`、または `xml` の列にフルテキスト インデックスを作成する場合は、型列を指定する必要があります。 *型列* は、各行のドキュメントのファイル拡張子 (.doc、.pdf、.xls など) を格納するテーブル列です。  
  
 フルテキスト インデックスを作成および保守するプロセスを *作成* ( *クロール*とも呼ばれます) といいます。 フルテキスト インデックスの作成には、完全作成、変更の追跡に基づく作成、およびタイムスタンプに基づく増分作成の 3 種類があります。 詳細については、「 [フルテキスト インデックスの作成](populate-full-text-indexes.md)」をご覧ください。  
  
##  <a name="common-tasks"></a><a name="tasks"></a>一般的なタスク  
 **フルテキストインデックスを作成するには**  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 **フルテキスト インデックスを変更するには**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 **フルテキスト インデックスを削除するには**  
  
-   [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql)  
  
 [このトピックの内容](#top)  
  
##  <a name="full-text-index-structure"></a><a name="structure"></a>フルテキストインデックスの構造  
 フルテキスト インデックスの構造をよく理解しておくことは、Full-Text Engine の動作を理解するのに役立ちます。 このトピックでは、 **の** Document [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] テーブルの抜粋をテーブル例として使用します。 この抜粋には、テーブルの 2 つの列 ( **DocumentID** 列および **Title** 列) と 3 つの行のみが含まれています。  
  
 この例では、 **Title** 列に対してフルテキスト インデックスが作成されているものとします。  
  
|DocumentID|Title|  
|----------------|-----------|  
|1|Crank Arm and Tire Maintenance|  
|2|Front Reflector Bracket and Reflector Assembly 3|  
|3|Front Reflector Bracket Installation|  
  
 たとえば、次のテーブル (フラグメント 1) は、 **Document** テーブルの **Title** 列に対して作成されたフルテキスト インデックスの内容を示しています。 フルテキスト インデックスには、この表に示されているより多くの情報が含まれています。 このテーブルは、フルテキスト インデックスの論理表現であり、例を挙げる目的で紹介しています。 行は、ディスクの使用量を最適化するために圧縮形式で格納されます。  
  
 データが元のドキュメントとは逆になっていることに注意してください。 これはキーワードがドキュメント ID にマップされているためです。 このため、フルテキスト インデックスは一般に逆インデックスと呼ばれます。  
  
 キーワード "and" がフルテキスト インデックスから削除されていることにも注意してください。 これは "and" がストップワードであり、フルテキスト インデックスからストップワードを削除することで、ディスク領域を大幅に節約し、クエリのパフォーマンスを向上させることができるためです。 ストップワードの詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。  
  
 **フラグメント 1**  
  
|キーワード|ColId|DocId|個数|  
|-------------|-----------|-----------|----------------|  
|Crank|1|1|1|  
|Arm|1|1|2|  
|Tire|1|1|4|  
|メンテナンス|1|1|5|  
|Front|1|2|1|  
|Front|1|3|1|  
|Reflector|1|2|2|  
|Reflector|1|2|5|  
|Reflector|1|3|2|  
|Bracket|1|2|3|  
|Bracket|1|3|3|  
|アセンブリ|1|2|6|  
|3|1|2|7|  
|インストール|1|3|4|  
  
 **Keyword** 列には、インデックス作成時に抽出された単一のトークン表現が含まれています。 ワード ブレーカーが、トークンの構成要素を決定します。  
  
 **ColId** 列には、フルテキスト インデックスが作成されている特定の列に対応する値が含まれています。  
  
 列には、 `DocId` フルテキストインデックスが作成されたテーブルの特定のフルテキストキー値にマップされる8バイトの整数値が含まれます。 このマッピングは、フルテキスト キーが整数データ型でない場合に必要になります。 このような場合、フルテキストキー値と値のマッピング `DocId` は、DocId マッピングテーブルと呼ばれる別のテーブルに保持されます。 これらのマッピングをクエリするには、 [sp_fulltext_keymappings](/sql/relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql) システム ストアド プロシージャを使用します。 検索条件を満たすには、上記の表の DocId 値と DocId Mapping テーブルを結合し、クエリ対象のベース テーブルから行を取得する必要があります。 ベース テーブルのフルテキスト キー値が整数データ型の場合は、その値を DocId として直接使用できるため、マッピングは必要ありません。 したがって、整数データ型のフルテキスト キー値を使用すると、フルテキスト クエリを最適化できます。  
  
 **Occurrence** 列には整数値が含まれます。 DocId 値ごとに、その DocId 内の特定キーワードの相対的な単語オフセットに対応するオカレンス値の一覧があります。 オカレンス値は、句または近接検索の判定に役立ちます。たとえば、句には数値の近いオカレンス値が含まれます。 また、関連性スコアを計算するのにも役立ちます。たとえば、DocId のキーワードのオカレンス数をスコアリングに使用できます。  
  
 [このトピックの内容](#top)  
  
##  <a name="full-text-index-fragments"></a><a name="fragments"></a>フルテキストインデックスフラグメント  
 論理フルテキスト インデックスは、通常、複数の内部テーブルに分割されます。 各内部テーブルは、フルテキスト インデックス フラグメントと呼ばれます。 これらのフラグメントの一部は、他のフラグメントよりも新しいデータを含んでいることがあります。 たとえば、DocId が 3 である次の行をユーザーが更新し、テーブルの変更が自動的に追跡される場合、新しいフラグメントが作成されます。  
  
|DocumentID|Title|  
|----------------|-----------|  
|3|Rear Reflector|  
  
 次に示すフラグメント 2 には、フラグメント 1 より新しい、DocId 3 に関するデータが含まれています。 したがって、ユーザーが "Rear Reflector" をクエリした場合、フラグメント 2 に含まれている DocId 3 のデータが使用されます。 各フラグメントには、 [sys.fulltext_index_fragments](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql) カタログ ビューを使用してクエリできる作成タイムスタンプが付いています。  
  
 **フラグメント 2**  
  
|キーワード|ColId|DocId|Occ|  
|-------------|-----------|-----------|---------|  
|Rear|1|3|1|  
|Reflector|1|3|2|  
  
 フラグメント 2 を見ればわかるように、フルテキスト クエリでは、各フラグメントを内部的にクエリし、古いエントリを破棄する必要があります。 したがって、非常に多くのフルテキスト インデックス フラグメントがフルテキスト インデックスに含まれている場合、クエリのパフォーマンスが大幅に低下する可能性があります。 フラグメントの数を減らすには、 [ALTER 全文カタログ](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)ステートメントの再構成オプションを使用して、フルテキストカタログを再構成し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。 このステートメントは *マスター マージ*を実行します。マスター マージでは、フラグメントが単一のより大きなフラグメントにマージされ、フルテキスト インデックスから古いエントリがすべて削除されます。  
  
 再構成が完了すると、次の行が例のインデックスに格納されます。  
  
|キーワード|ColId|DocId|Occ|  
|-------------|-----------|-----------|---------|  
|Crank|1|1|1|  
|Arm|1|1|2|  
|Tire|1|1|4|  
|メンテナンス|1|1|5|  
|Front|1|2|1|  
|Rear|1|3|1|  
|Reflector|1|2|2|  
|Reflector|1|2|5|  
|Reflector|1|3|2|  
|Bracket|1|2|3|  
|アセンブリ|1|2|6|  
|3|1|2|7|  
  
 [このトピックの内容](#top)  
  
  
