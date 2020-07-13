---
title: フルテキスト検索に使用するストップワードとストップリストの構成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 103b5024368c5ca239856580e9b45473aabf6a92
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997645"
---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a>フルテキスト検索に使用するストップワードとストップリストの構成と管理
  フルテキスト インデックスが肥大化するのを防ぐため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、頻繁に出現する、検索に役立たない文字列を破棄するメカニズムがあります。 破棄されるこのような文字列を *ストップワード*と呼びます。 インデックスの作成中、Full-Text Engine により、フルテキスト インデックスからストップワードが除外されます。 つまり、フルテキスト クエリでは、ストップワードが検索されません。  
  
##  <a name="understanding-stopwords-and-stoplists"></a><a name="understand"></a>ストップワードとストップリストについて  
 ストップワードは、特定の言語で意味を持つ単語の場合や言語的な意味のない *トークン* の場合があります。 たとえば、英語では、"a"、"and"、"is"、"the" などの単語は、検索に役立たないことが知られているため、フルテキスト インデックスから除外されます。  
  
 含まれるストップワードは無視されますが、フルテキスト インデックスではその位置が考慮されます。 たとえば、"Instructions are applicable to these Adventure Works Cycles models" という句があるとします。 以下のテーブルは、句の中の語の位置を表しています。  
  
|Word|位置|  
|----------|--------------|  
|Instructions|1|  
|are|2|  
|applicable|3|  
|to|4|  
|these|5|  
|Adventure|6|  
|Works|7|  
|Cycles|8|  
|モデル|9|  
  
 位置 2、4、および 5 にあるストップワード "are"、"to"、"these" は、フルテキスト インデックスから除外されます。 ただし、その位置情報は保持されるため、語句内の他の語の位置は変わりません。  
  
 ストップワードは、ストップリストと呼ばれるオブジェクトを使用してデータベースで管理されます。 *ストップリスト* は、フルテキスト インデックスに関連付けられている場合、そのインデックスのフルテキスト クエリに適用されるストップワードの一覧です。  
  
  
##  <a name="creating-a-stoplist"></a><a name="creating"></a>ストップリストの作成  
 ストップリストは、次のいずれかの方法で作成できます。  
  
-   システムに備わっているストップリストをデータベースで使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、最も頻繁に使用するストップワードを含むシステム ストップリストが、サポート対象の言語ごとに用意されています。つまり、既定で、特定のワード ブレーカーに関連付けられている言語ごとにストップリストが用意されています。 システム ストップリストには、サポートされているすべての言語に対して一般的なストップワードが含まれています。  システム ストップリストをコピーし、ストップワードを追加したり削除したりすることにより、そのコピーをカスタマイズできます。  
  
     システム ストップリストは [Resource](../databases/resource-database.md) データベースにインストールされます。  
  
-   指定した任意の言語について独自のストップリストを作成した後、ストップワードを追加します。 必要に応じて、ストップリストからストップワードを削除することもできます。  
  
-   現在のサーバー インスタンスで他のデータベースの既存のカスタム ストップリストを使用して、必要に応じて、ストップワードを追加および削除します。  
  
 **ストップリストを作成するには**  
  
-   [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
#### <a name="to-create-a-full-text-stoplist-in-management-studio"></a>Management Studio でフルテキスト ストップリストを作成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開します。  
  
2.  **[データベース]** を展開し、フルテキスト ストップリストを作成する対象のデータベースを展開します。  
  
3.  **[ストレージ]** を展開し、 **[フルテキスト ストップリスト]** を右クリックします。  
  
4.  **[新しいフルテキスト ストップリスト]** をクリックします。  
  
5.  ストップリスト名を指定します。  
  
6.  必要に応じて、他のユーザーをストップリストの所有者として指定します。  
  
7.  次に示すストップリスト作成オプションのいずれかを選択します。  
  
    -   **[空のストップリストを作成する]**  
  
    -   **[システム ストップリストから作成する]**  
  
    -   **[既存のフルテキスト ストップリストから作成する]**  
  
     詳細については、「[新しいフルテキスト ストップリスト &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 **ストップリストを削除するには**  
  
-   [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
##  <a name="using-a-stoplist-in-full-text-queries"></a><a name="queries"></a>フルテキストクエリでのストップリストの使用  
 ストップリストをクエリで使用するには、ストップリストをフルテキスト インデックスに関連付ける必要があります。 インデックスの作成時にストップリストをフルテキスト インデックスにアタッチしたり、後でインデックスを変更してストップリストを追加したりできます。  
  
 **フルテキスト インデックスを作成してストップリストを関連付けるには**  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 **既存のフルテキスト インデックスに対してストップリストの関連付けまたは関連付け解除を行うには**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 **ストップワードが原因でフルテキスト クエリのブール演算が失敗する場合に、エラー メッセージを非表示にするには**  
  
-   [transform noise words サーバー構成オプション](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
  
##  <a name="viewing-stoplists-and-stoplist-metadata"></a><a name="viewing"></a>ストップリストとストップリストメタデータの表示  
 **ストップリストのすべてのストップワードを表示するには**  
  
-   [sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 **現在のデータベース内にあるすべてのストップリストに関する情報を取得するには**  
  
-   [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 **ワード ブレーカー、類語辞典、およびストップリストの組み合わせによるトークン化の結果を表示するには**  
  
-   [dm_fts_parser &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="changing-the-stopwords-in-a-stoplist"></a><a name="change"></a>ストップリスト内のストップワードの変更  
 **ストップリストからストップワードを追加または削除するには**  
  
-   [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
#### <a name="to-change-the-stopwords-in-a-stoplist-in-management-studio"></a>Management Studio でストップリスト内のストップワードを変更するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開します。  
  
2.  **[データベース]** を展開し、データベースを展開します。  
  
3.  **[ストレージ]** を展開し、 **[フルテキスト ストップリスト]** をクリックします。  
  
4.  プロパティを変更するストップリストを右クリックし、 **[プロパティ]** をクリックします。  
  
5.  [[フルテキスト ストップリストのプロパティ]](../../database-engine/full-text-stoplist-properties.md) ダイアログ ボックスで:  
  
    1.  **[アクション]** ボックスの一覧で、 **[ストップワードの追加]**、 **[ストップワードの削除]**、 **[すべてのストップワードの削除]**、 **[ストップリストのクリア]** のいずれかのアクションを選択します。  
  
    2.  選択したアクションに対して **[ストップワード]** ボックスが有効になっている場合は、単一のストップワードを入力します。 このストップワードは一意である必要があります。つまり、選択した言語で、このストップリストにまだ含まれていないものである必要があります。  
  
    3.  選択したアクションに対して **[フルテキスト言語]** ボックスの一覧が有効になっている場合は、言語を選択します。  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
##  <a name="upgrading-noise-words-from-sql-server-2005"></a><a name="upgrade"></a>SQL Server 2005 からのノイズワードのアップグレード  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] のノイズ ワードは、ストップワードになりました。 データベースが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]からアップグレードされると、ノイズ ワード ファイルは使用されなくなります。 ただし、ノイズ ワード ファイルは FTDATA\ FTNoiseThesaurusBak フォルダーに保存され、後で更新する際、または対応するストップリストを作成する際に使用できます。 ノイズ ワード ファイルをストップリストにアップグレードする方法の詳細については、「 [フルテキスト検索のアップグレード](upgrade-full-text-search.md)」を参照してください。  
  
  
  
