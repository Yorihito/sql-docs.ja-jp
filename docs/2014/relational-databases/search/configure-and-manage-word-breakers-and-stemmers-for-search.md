---
title: 検索用のワード ブレーカーとステマーの構成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- full-text search [SQL Server], stemmers
- linguistic analysis [full-text search]
- full-text indexes [SQL Server], linguistic analysis
- full-text search [SQL Server], word breakers
- default full-text language option
- stemmers [full-text search]
- conjugating verbs [full-text search]
- word breakers [full-text search]
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 22cb7371a0215989d2759ddfb2c84f51ba5c3c31
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997579"
---
# <a name="configure-and-manage-word-breakers-and-stemmers-for-search"></a>検索用のワード ブレーカーとステミング機能の構成と管理
  ワード ブレーカーとステミング機能は、すべてのフルテキスト インデックス データに対して言語分析を実行します。 言語分析には、単語の境界 (単語の区切り) の検索と動詞の活用 (ステミング) が含まれます。 ワード ブレーカーとステミング機能は言語に固有のものであり、言語分析の規則は言語によって異なります。 特定の言語において、 *ワード ブレーカー* によって、言語の語彙の規則に基づいて単語の境界を検出し、個々の単語を識別します。 各単語 ( *トークン*ともいいます) は、サイズを縮小するために圧縮された表現でフルテキスト インデックスに挿入されます。 *ステミング機能* はその言語の規則に基づいて特定の語の変化形を生成します (たとえば、"running"、"ran"、"runner" は、"run" という語の変化形です)。  
  
 言語固有のワード ブレーカーを使用すると、その言語に対する検索結果の精度が高くなります。 言語ファミリにはワード ブレーカーが存在していても、特定のサブ言語は対象とされない場合は、主言語が使用されます。 たとえば、カナダ系フランス語テキストの処理には、フランス語のワード ブレーカーが使用されます。 特定の言語用のワード ブレーカーが使用できない場合は、ニュートラル ワード ブレーカーが使用されます。 ニュートラル ワード ブレーカーを使用すると、単語は空白や句読点などのニュートラル文字で分割されます。  
  
##  <a name="registering-word-breakers"></a><a name="register"></a>ワードブレーカーの登録  
 言語のワード ブレーカーを使用する場合は、そのワード ブレーカーを登録する必要があります。 登録されているワードブレーカーでは、関連する言語リソース (ステミング機能、ノイズワード (ストップワード)、類義語辞典ファイル) もフルテキストインデックス作成およびクエリ操作で使用できるようになります。 現在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にワード ブレーカーが登録されている言語の一覧を表示するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
 SELECT * FROM sys.fulltext_languages  
  
 ワード ブレーカーを追加、削除、または変更すると、フルテキスト インデックスおよびフルテキスト クエリでサポートされている Microsoft Windows のロケール識別子 (LCID) の一覧を更新する必要があります。 詳細については、「 [登録済みのフィルターおよびワード ブレーカーの表示または変更](view-or-change-registered-filters-and-word-breakers.md)」を参照してください。  
  
##  <a name="setting-the-default-full-text-language-option"></a><a name="default"></a>[既定のフルテキスト言語] オプションの設定  
 のローカライズ版では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 適切な一致が存在する場合、セットアップによって `default full-text language` オプションがサーバーの言語に設定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズされていないバージョンでは、`default full-text language` オプションは英語になります。  
  
 フルテキスト インデックスを作成または変更する際には、フルテキスト インデックス列ごとに言語を指定できます。 列に言語が指定されていない場合、既定では構成オプション `default full-text language` の値になります。  
  
> [!NOTE]  
>  1 つのフルテキスト クエリ関数句に指定されるすべての列は、クエリで LANGUAGE オプションが指定されていない限り、同じ言語を使用する必要があります。 クエリ対象のフルテキスト インデックスが付けられた列に使用する言語によって、フルテキスト クエリの述語 ([CONTAINS](/sql/t-sql/queries/contains-transact-sql) および [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)) および関数 ([CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) および [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)) の引数に対して実行される言語分析が決まります。  
  
##  <a name="choosing-the-language-for-an-indexed-column"></a><a name="lang"></a>インデックス付き列の言語の選択  
 フルテキスト インデックスを作成する際には、各インデックス列に対して言語を指定することをお勧めします。 列に言語が指定されていない場合、システムの既定の言語が使用されます。 列のインデックス作成に使用されるワード ブレーカーとステミング機能は、列の言語によって決まります。 また、指定した言語の類義語辞典ファイルが、列のフルテキスト クエリで使用されます。  
  
 フルテキスト インデックスの作成時に列の言語を選択する際には、注意点が 2 つあります。 これらの注意点は、テキストをトークン化する方法と、Full-Text Engine によるインデックス作成の方法にかかわるものです。 詳細については、「 [フルテキスト インデックス作成時の言語の選択](choose-a-language-when-creating-a-full-text-index.md)」を参照してください。  
  
 **列のワード ブレーカーの言語を表示するには**  
  
-   [フルテキスト インデックスの管理](../indexes/indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="obtaining-information-about-word-breakers"></a><a name="info"></a>ワードブレーカーに関する情報の取得  
 **ワードブレーカー、類義語辞典、およびストップリストの組み合わせによるトークン化の結果の表示**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
 **登録されているワード ブレーカーに関する情報を返すには**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="troubleshooting-word-breaking-time-out-errors"></a><a name="tshoot"></a>単語区切りのタイムアウトエラーのトラブルシューティング  
 単語区切りのタイムアウト エラーは、さまざまな状況で発生する可能性があります。 エラーが発生する状況とその対処方法については、「 [MSSQLSERVER_30053](../errors-events/mssqlserver-30053-database-engine-error.md)」を参照してください。  
  
##  <a name="understanding-the-impact-of-new-word-breakers"></a><a name="impact"></a>新しいワードブレーカーの影響について  
 各バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、通常、新しいワード ブレーカーが含まれています。これらのワード ブレーカーでは、言語の規則が改良されているため、以前のワード ブレーカーよりも精度が向上しています。 新しいワード ブレーカーは、前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からインポートされたフルテキスト インデックスのワード ブレーカーとは少し動作が異なる場合もあります。 データベースが現在のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードされたときにフルテキスト カタログをインポートした場合は、この動作の違いが重要になります。 フルテキスト カタログのフルテキスト インデックスで使用される 1 つまたは複数の言語が、新しいワード ブレーカーに関連付けられる可能性があります。 詳細については、「 [フルテキスト検索のアップグレード](upgrade-full-text-search.md)」を参照してください。  
  
 すべてのワードブレーカーの完全な一覧については、「 [sys. fulltext_languages &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のフルテキストインデックスの変更](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [sp_fulltext_service &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)   
 [fulltext_languages &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [フルテキスト検索のためのストップワードとストップリストの構成と管理](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [フルテキスト検索のアップグレード](upgrade-full-text-search.md)  
  
  
