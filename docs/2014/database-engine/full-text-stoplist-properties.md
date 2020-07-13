---
title: フルテキストストップリストのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff27a1258d5164e3e93d34b6ff757993d6f6363
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932943"
---
# <a name="full-text-stoplist-properties"></a>[フルテキスト ストップリストのプロパティ]
  このダイアログ ボックスを使用すると、個々のストップワードの追加や削除、特定の言語のすべてのストップワードの削除、および現在のストップリストのクリアを実行できます。 ストップワードは、ストップリストで一般的に使用される単語です。 ストップリスト内のストップワードは、ストップリストを使用するテーブルのフルテキスト インデックスから省略されます。 詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)」を参照してください。  
  
 **SQL Server Management Studio を使用してストップリストのプロパティを変更するには**  
  
-   [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>オプション  
 **動作**  
 実行するアクションを指定します。  
  
 **[ストップワードの追加]**  
 一般的に使用される単語をストップリストに追加します。  
  
 **[ストップワードの削除]**  
 ストップリストからストップワードを削除します。  
  
 **[すべてのストップワードの削除]**  
 特定の言語のストップワードをすべて削除します。  
  
 **[ストップリストのクリア]**  
 すべての言語のストップワードをすべて削除することによって、ストップリストをクリアします。  
  
 **ストップワード**  
 **[ストップワードの追加]** または **[ストップワードの削除]** を選択した場合は、 **[ストップワード]** フィールドにストップワードを入力します。 新しいストップワードは一意である、つまり、選択した言語のこのストップリストにまだ含まれていない必要があります。  
  
 **[フルテキスト言語]**  
 **[ストップワードの追加]**、 **[ストップワードの削除]**、または **[すべてのストップワードの削除]** を選択した場合は、このリスト ボックスから、操作対象のストップワードの言語を選択します。 このリスト ボックスには、サーバー インスタンスでサポートされているすべてのフルテキスト言語が表示されます。  
  
## <a name="see-also"></a>参照  
 [fulltext_stopwords &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)   
 [fulltext_stoplists &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)   
 [フルテキスト検索のためのストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)   
 [Transact-sql&#41;&#40;フルテキストストップリストの変更](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [Transact-sql&#41;&#40;のフルテキストストップリストの作成](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
