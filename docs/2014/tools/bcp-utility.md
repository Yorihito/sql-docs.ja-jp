---
title: bcp ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server]
- exporting data
- row exporting [SQL Server]
- copying data [SQL Server], bcp utility
- command prompt utilities [SQL Server], bcp
- tables [SQL Server], importing data
- column importing [SQL Server]
- bcp utility [SQL Server], command options
- file exporting [SQL Server]
- bulk copy [SQL Server]
- bcp utility [SQL Server], about bcp utility
- tables [SQL Server], exporting data
- row importing [SQL Server]
- importing data, bcp utility
- file importing [SQL Server]
- column exporting [SQL Server]
ms.assetid: c0af54f5-ca4a-4995-a3a4-0ce39c30ec38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ddc4c4e7023a83bfde9295a1410e7db5cb90b84
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008736"
---
# <a name="bcp-utility"></a>bcp ユーティリティ
  **Bcp**ユーティリティは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー指定の形式でのインスタンスとデータファイルとの間でデータの一括コピーを行います。 **bcp** ユーティリティを使うと、多数の新規行を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルにインポートしたり、データをテーブルからデータ ファイルにエクスポートしたりできます。 このユーティリティでは **の知識は必要ありません。ただし、** queryout [!INCLUDE[tsql](../includes/tsql-md.md)]オプションと同時に使う場合はその知識が必要になります。 データをテーブルにインポートするには、そのテーブル用に作成されたフォーマット ファイルを使用するか、テーブルの構造およびテーブルの列に有効なデータの型を理解しておく必要があります。  
  
 ![トピック リンク アイコン](../../2014/database-engine/media/topic-link.gif "トピック リンク アイコン")**bcp** 構文で使用される構文表記規則については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」をご覧ください。  
  
> [!NOTE]  
>  **bcp** を使ってデータをバックアップする場合、フォーマット ファイルを作成してデータ形式を記録します。 **bcp** データ ファイルには、スキーマ情報やフォーマット情報が 含まれない ので、テーブルまたはビューが削除され、フォーマット ファイルがない場合は、データをインポートできないことがあります。  
  
## <a name="syntax"></a>構文  
  
```  
  
   bcp [database_name.] schema.{table_name | view_name | "query" {indata_file | outdata_file | queryoutdata_file | format nul}  
  
[-apacket_size]  
[-bbatch_size]  
[-c]  
[-C { ACP | OEM | RAW | code_page } ]  
[-ddatabase_name]  
[-eerr_file]  
[-E]  
[-fformat_file]  
[-Ffirst_row]  
[-h"hint [,...n]"]   
[-iinput_file]  
[-k]  
[-Kapplication_intent]  
[-Llast_row]  
[-mmax_errors]  
[-n]  
[-N]  
[-ooutput_file]  
[-Ppassword]  
[-q]  
[-rrow_term]  
[-R]  
[-S [server_name[\instance_name]]  
[-tfield_term]  
[-T]  
[-Ulogin_id]  
[-v]  
[-V (80 | 90 | 100 | 110)]  
[-w]  
[-x]  
/?  
```  
  
## <a name="arguments"></a>引数  
 *data_file*  
 データ ファイルの完全パスを指定します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]にデータを一括インポートする場合は、データ ファイルには指定したテーブルまたはビューにコピーするデータが含まれます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]からデータを一括エクスポートする場合は、データ ファイルにはテーブルまたはビューからコピーしたデータが含まれます。 パスは、1 文字から 255 文字までです。 データファイルには、最大で 2<sup>63</sup> -1 行を含めることができます。  
  
 *database_name*  
 指定したテーブルまたはビューを含むデータベースの名前を指定します。 指定しない場合は、ユーザーの既定データベースになります。  
  
 `d-` で明示的にデータベース名を指定することもできます。  
  
 **in** _data_file_  |  **out**_data_file_  |  **queryout**_data_file_  |  **形式 nul**  
 次に示すように、一括コピーの方向を指定します。  
  
-   **in** はファイルからデータベース テーブルまたはビューへのコピーを行います。  
  
-   **out** はデータベース テーブルまたはビューからファイルへのコピーを行います。 既存のファイルを指定すると、ファイルは上書きされます。 **bcp** ユーティリティは、データを抽出するときに、空文字列を NULL 文字列で、NULL 文字列を空文字列で表すことに注意してください。  
  
-   **queryout** はクエリからのコピーを行います。データをクエリから一括コピーする場合にのみ指定する必要があります。  
  
-   **format**は、指定されたオプション (**-n**、 `-c` 、 `-w` 、または **-n**) と、テーブルまたはビューの区切り記号に基づいてフォーマットファイルを作成します。 **Bcp**コマンドは、データを一括コピーするときにフォーマットファイルを参照できます。フォーマットファイルを使用すると、書式情報を対話的に再入力する必要がありません。 **format** オプションには **-f** オプションが必要です。XML フォーマット ファイルを作成する場合には、 **-x** オプションも必要です。 詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)」をご覧ください。 値として **nul** を指定する必要があります (**format nul**)。  
  
 *owner*  
 テーブルまたはビューの所有者の名前を指定します。 操作を実行するユーザーが指定のテーブルまたはビューを所有している場合、*owner* は省略可能です。 *owner* が指定されず、操作を実行するユーザーが指定のテーブルまたはビューを所有していない場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] からエラー メッセージが返され、操作は取り消されます。  
  
 **"** _クエリ_ **"**  
 結果セットを返す単一の [!INCLUDE[tsql](../includes/tsql-md.md)] クエリです。 クエリから複数の結果セットが返される場合、最初の結果セットのみがデータ ファイルにコピーされ、それ以降の結果セットは無視されます。 クエリは二重引用符で、クエリに埋め込まれたものは単一引用符で囲みます。 クエリからデータを一括コピーする場合には、**queryout** も指定する必要があります。  
  
 ストアド プロシージャ内で参照されるテーブルのすべてが bcp ステートメントの実行前に存在する場合に限り、クエリはストアド プロシージャを参照できます。 たとえば、ストアド プロシージャにより一時テーブルが生成される場合、この一時テーブルは実行時にだけ利用でき、ステートメントの実行時には利用できないため、 **bcp** ステートメントは失敗します。 このような場合、ストアド プロシージャの結果をテーブルに挿入し、 **bcp** を使用してテーブルからデータ ファイルにデータをコピーすることを検討してください。  
  
 *table_name*  
 データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にインポートする (**in**) 場合はインポート先のテーブルの名前、データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] からエクスポートする (**out**) 場合はエクスポート元のテーブルの名前です。  
  
 *view_name*  
 データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にコピーする (**in**) 場合はコピー先のビューの名前、データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] からコピーする (**out**) 場合はコピー元のビューの名前です。 すべての列が同じテーブルを参照しているビューのみが、コピー先のビューとして使用できます。 ビューにデータをコピーするときの制限の詳細については、「[挿入 &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)」をご覧ください。  
  
 **-a** _packet_size_  
 サーバーとの間で送信されるネットワーク パケットごとのバイト数を指定します。 サーバー構成オプションは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (または **sp_configure** システム ストアド プロシージャ) を使用して設定できます。 ただし、このオプションを使用すると、サーバー構成オプションを個別にオーバーライドできます。 *packet_size* の有効値は 4,096 から 65,535 バイトです。既定値は 4,096 です。  
  
 パケット サイズを大きくすると、一括コピーのパフォーマンスを向上させることができます。 より大きなサイズのパケットを要求しても、許可されない場合、既定値が使用されます。 **bcp** ユーティリティが生成するパフォーマンス統計には、使用したパケット サイズが示されます。  
  
 **-b** _batch_size_  
 一括インポートするデータの行数を指定します。 コミットされる前に、各バッチはすべてのバッチをインポートする個別のトランザクションとしてインポートおよび記録されます。 既定では、データ ファイルのすべての行が 1 つのバッチとしてインポートされます。 複数のバッチに行を分散するには、データ ファイルの行数よりも少ない *batch_size* を指定します。 バッチのトランザクションが失敗すると、現在のバッチの挿入のみがロールバックされます。 コミットされたトランザクションによって既にインポートされているバッチは、それ以降の失敗による影響を受けません。  
  
 このオプションは、 **-h "** ROWS_PER_BATCH ** = *`bb`* "** オプションと組み合わせて使用しないでください。  
  
 `-c`  
 文字データ型を使用して操作を実行します。 このオプションでは、フィールドごとにプロンプトは表示されません。プレフィックスなしのストレージ型としてを使用し `char` 、フィールド区切り記号として**\t** (タブ文字) を、行ターミネータに**\r\n** (改行文字) を使用します。 `-c` と `-w` には互換性がありません。  
  
 詳細については、「[文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)」をご覧ください。  
  
 **-C** { **ACP** | **OEM** | **RAW** | *code_page* }  
 データ ファイル内のデータのコード ページを指定します。 *code_page*は `char` 、 `varchar` `text` 文字値が127より大きい、または32未満の列がデータに含まれている場合にのみ該当します。  
  
> [!NOTE]  
>  フォーマット ファイルの各列に対して照合順序名を指定することをお勧めします。  
  
|コード ページ値|説明|  
|---------------------|-----------------|  
|ACP|[!INCLUDE[vcpransi](../includes/vcpransi-md.md)]/Microsoft Windows (ISO 1252)。|  
|OEM|クライアントが使用する既定のコード ページです。 **-C** が指定されていない場合に使用される既定のコード ページです。|  
|RAW|コード ページの変換は行われません。 したがって、これは最も速いオプションです。|  
|*code_page*|850 などの特定のコード ページ番号を指定します。<br /><br /> **&#42;&#42; の重要な &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では、コードページ 65001 (UTF-8 エンコード) はサポートされていません。|  
  
 `-d` *database_name*  
 接続先のデータベースを指定します。 既定では、bcp.exe はユーザーの既定のデータベースに接続します。 `-d` *Database_name*と3つの部分で構成される名前 (*database_name*bcp.exe に最初のパラメーターとして渡される) が指定されている場合、データベース名を2回指定することはできないため、エラーが発生します。*Database_name*がハイフン (-) またはスラッシュ (/) で始まる場合は、とデータベース名の間に空白を追加しないで `-d` ください。  
  
 **-e** _err_file_  
 **bcp** ユーティリティがファイルからデータベースに転送できなかったすべての行を格納するエラー ファイルの完全パスを指定します。 **bcp** コマンドからのエラー メッセージは、ユーザーのワークステーションに送られます。 このオプションを指定しないと、エラー ファイルは作成されません。  
  
 *err_file* がハイフン (-) またはスラッシュ (/) で始まる場合は、 **-e** と *err_file* 値の間に空白を入れないでください。  
  
 **-E**  
 インポートしたデータ ファイルの ID 値 (複数可) を ID 列に使用することを指定します。 **-E** を指定しない場合、インポートされるデータ ファイルのこの列の ID 値は無視され、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はテーブルの作成時に指定されたシードと増分の値に基づいて一意の値を自動的に割り当てます。  
  
 データ ファイルにテーブルまたはビュー内の ID 列の値が含まれない場合は、フォーマット ファイルを使用して、データのインポート時にテーブルまたはビュー内の ID 列を無視するように指定します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、一意な値が自動的にこの列に割り当てられます。 詳細については、「[DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)」をご覧ください。  
  
 **-E** オプションには、特別な権限が必要です。 詳細については、後の「解説」を参照してください。  
  
 **-f** _format_file_  
 フォーマット ファイルの完全パスを指定します。 このオプションの意味は、オプションが使用されている環境によって次のように異なります。  
  
-   **-f** を **format** オプションと共に使用した場合、指定されたテーブルまたはビューに対して、指定された *format_file* が作成されます。 XML フォーマット ファイルを作成するには、 **-x** オプションも指定します。 詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)」をご覧ください。  
  
-   **in** または **out** オプションと共に使用する場合、 **-f** を使うには既存のフォーマット ファイルが必要です。  
  
    > [!NOTE]  
    >  **in** または **out** オプションを使う場合、フォーマット ファイルは省略可能です。 - **F**オプションがない場合、 **-n**、 `-c` 、 `-w` 、または **-n**が指定されていない場合、コマンドはフォーマット情報を要求し、応答をフォーマットファイル (既定のファイル名は .bcp. fmt) に保存します。  
  
 *format_file* がハイフン (-) またはスラッシュ (/) で始まる場合は、 **-f** と *format_file* 値の間に空白を入れないでください。  
  
 **-F** _first_row_  
 テーブルからエクスポートする最初の行、またはデータ ファイルからインポートする最初の行の番号を指定します。 このパラメーターには、(>) 0 よりも大きい値を指定する必要があります。ただし、合計行数は、() の値よりも小さい ( \< ) か、または (=) 以下です。 このパラメーターがない場合、既定ではファイルの最初の行となります。  
  
 *first_row* には、2^63-1 以下の正の整数を指定できます。 **-F**_first_row_ は 1 から始まります。  
  
 **-h"** _hint_[ **,**... *n*] **"**  
 データをテーブルまたはビューに一括インポートするときに使用するヒントを指定します。  
  
 ORDER **(**_列_[ASC |DESC] [**,**...*n*]**)**  
 データ ファイルのデータの並べ替え順序です。 インポートするデータをテーブル上のクラスター化インデックスに従って並べ替えると、一括インポートのパフォーマンスが向上します。 データ ファイルが異なる順序で並べ替えられている場合、つまり、クラスター化インデックス キーの順序以外で並べ替えられている場合、またはテーブルにクラスター化インデックスが存在しない場合、ORDER 句は無視されます。 指定する列の名前は、インポート先のテーブル内で有効な列の名前であることが必要です。 既定では、 **bcp** はデータ ファイルの並べ替えが行われていないことを前提としています。 最適な一括インポートのため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、インポートするデータが並べ替えられているかどうかも検証されます。  
  
 ROWS_PER_BATCH **=** _bb_  
 各バッチあたりのデータ行数 ( *bb*) です。 **-b** を指定しない場合に使うと、データ ファイル全体が 1 つのトランザクションとしてサーバーに送られます。 サーバーは、 *bb*の値に応じて一括コピーの負荷を最適化します。 ROWS_PER_BATCH の既定値はありません。  
  
 KILOBYTES_PER_BATCH **=** _cc_  
 バッチごとのデータの概算キロバイト数 (KB) です ( *cc*)。 KILOBYTES_PER_BATCH の既定値はありません。  
  
 TABLOCK  
 一括読み込み操作中に一括更新のテーブルレベルのロックが適用されます。これを指定しない場合、行レベルのロックが適用されます。 一括コピー操作時だけロックすることにより、テーブル ロックの競合が少なくなるので、このヒントはパフォーマンスを大幅に向上させます。 テーブルにインデックスがなく、 **TABLOCK** を指定した場合は、複数のクライアントで同時に 1 つのテーブルを読み込むことができます。 既定では、ロック動作はテーブル オプション **table lock on bulk load**によって決定されます。  
  
 CHECK_CONSTRAINTS  
 一括インポート操作中、対象テーブルまたはビューに対するすべての制約を検証します。 CHECK_CONSTRAINTS ヒントを指定しない場合、CHECK 制約および FOREIGN KEY 制約は無視され、操作の後でテーブルの制約は信頼されていないものとしてマークされます。  
  
> [!NOTE]  
>  UNIQUE、PRIMARY KEY、および NOT NULL 制約は常に適用されます。  
  
 テーブル全体の制約は、任意の時点で必ず検証してください。 一括インポート操作の前にテーブルが空でなかった場合、制約を再検証するコストは、増分データに CHECK 制約を適用するコストを超える場合があります。 したがって、通常は、増分一括インポート時の制約チェックを有効にすることをお勧めします。  
  
 入力データに制約違反の行が含まれている場合などは、制約を無効 (既定の動作) にできます。 CHECK 制約を無効にした場合、データをインポートした後で、 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを使用して無効なデータを削除できます。  
  
> [!NOTE]  
>  **bcp** によってデータ検証とデータ チェックが実行されるようになったため、無効なデータを含むデータ ファイルに対して実行した場合、このスクリプトは失敗する可能性があります。  
  
> [!NOTE]  
>  **-m** _max_errors_ スイッチは、制約チェックには適用されません。  
  
 FIRE_TRIGGERS  
 **in** 引数と共に指定されている場合、一括コピーの操作時に、コピー先のテーブル上で定義されている挿入トリガーを実行します。 FIRE_TRIGGERS が指定されていない場合は、挿入トリガーは実行されません。 FIRE_TRIGGERS は、 **out**引数、 **queryout**引数、および **format** 引数では無視されます。  
  
 **-i** _input_file_  
 対話モード (**-n**、 `-c` 、 `-w` 、または **-n**が指定されていない) を使用して一括コピーを実行する場合の、各データフィールドに対するコマンドプロンプトの質問への応答を含む応答ファイルの名前を指定します。  
  
 *input_file* がハイフン (-) またはスラッシュ (/) で始まる場合は、 **-i** と *input_file* 値の間に空白を入れないでください。  
  
 **-k**  
 一括コピー操作時、空の列には、挿入される列の既定値ではなく、NULL 値が保持されます。 詳細については、「[一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)」をご覧ください。  
  
 **-K** _application_intent_  
 アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は、 **ReadOnly**だけです。 **-K** を指定しない場合、bcp ユーティリティでは AlwaysOn 可用性グループのセカンダリ レプリカへの接続がサポートされません。 詳細については、「[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ (AlwaysOn 可用性グループ)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 **-L** _last_row_  
 テーブルからエクスポートする最後の行、またはデータ ファイルからインポートする最後の行の番号を指定します。 このパラメーターには、(>) 0 よりも大きい値を指定する必要がありますが、() より小さい \< か、または最後の行の番号に等しい (=)。 このパラメーターがない場合、既定ではファイルの最後の行となります。  
  
 *last_row* には、2^63-1 以下の正の整数を指定できます。  
  
 **-m** _max_errors_  
 **bcp** 操作が取り消される前に発生可能な構文エラーの最大数を指定します。 構文エラーは、対象となるデータ型へのデータの変換エラーを意味しています。 *max_errors* の合計では、制約違反など、サーバーでのみ検出できるエラーはすべて対象外となります。  
  
 **bcp** ユーティリティでコピーできない行は無視され、1 つのエラーとしてカウントされます。 このオプションが指定されない場合の既定値は 10 になります。  
  
> [!NOTE]  
>  **-M**オプションは、 `money` データ型またはデータ型の変換にも適用されません `bigint` 。  
  
 **-n**  
 データのネイティブ (データベース) データ型を使用して一括コピー操作を実行します。 このオプションを使用すると、フィールドごとにプロンプトが表示されません。ネイティブ値が使用されます。  
  
 詳細については、「[ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)」をご覧ください。  
  
 **-N**  
 文字以外のデータについてはデータベースのネイティブなデータ型を使用し、文字データについては Unicode 文字を使用して、一括コピー操作を実行します。 `-w` オプションの代わりにこのオプションを使用すると、高いパフォーマンスが得られます。このオプションは、データ ファイルを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスから別のインスタンスにデータを転送する場合に使用します。 フィールドごとにプロンプトは表示されません。 ANSI 拡張文字を含むデータを転送し、ネイティブ モードのパフォーマンスを利用する場合は、このオプションを使用します。  
  
 詳細については、「 [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)」をご覧ください。  
  
 **-N**を使用して bcp.exe を使用して同じテーブルスキーマにデータをエクスポートしてからインポートした場合、固定長の Unicode 以外の文字の列 (など) があると、切り捨ての警告が表示されることがあり `char(10)` ます。  
  
 この警告は、無視してもかまいません。 この警告を解決するには、 **-N** ではなく **-n**を使用する方法があります。  
  
 **-o** _output_file_  
 コマンド プロンプトからリダイレクトされた出力を受け取るファイル名を指定します。  
  
 *output_file* がハイフン (-) またはスラッシュ (/) で始まる場合は、 **-o** と *output_file* 値の間に空白を入れないでください。  
  
 **-P** _password_  
 ログイン ID のパスワードを指定します。 このオプションを指定しない場合、 **bcp** コマンドによってパスワードが要求されます。 また、このオプションをコマンド プロンプトの最後にパスワードなしで使用すると、 **bcp** では既定のパスワード (NULL) が使用されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../includes/ssnotestrongpass-md.md)]  
  
 パスワードをマスクする場合は、 **-P** オプションを **-U** オプションと共に指定しないでください。 **bcp** を **-U** オプションおよび他のスイッチと共に指定した後 ( **-P**は指定しない)、Enter キーを押すと、このコマンドによってパスワードが要求されます。 この方法を使用すると、入力時にパスワードが確実にマスクされます。  
  
 *password* がハイフン (-) またはスラッシュ (/) で始まる場合は、 **-P** と *password* 値の間に空白を入れないでください。  
  
 `-q`  
 **bcp** ユーティリティと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンス間の接続で、SET QUOTED_IDENTIFIERS ON ステートメントを実行します。 名前に空白や単一引用符が含まれるデータベース、所有者、テーブル、またはビューを指定する場合に、このオプションを使用します。 3 つの要素から成るテーブル名またはビュー名全体を、二重引用符 (" ") で囲みます。  
  
 空白や単一引用符を含むデータベース名を指定するには、 **-q** オプションを使用する必要があります。  
  
 `-q` は、`-d` に渡される値には適用されません。  
  
 詳細については、後の「解説」を参照してください。  
  
 **-r** _row_term_  
 行ターミネータを指定します。 既定値は **\n** (改行文字) です。 既定の行ターミネータをオーバーライドする場合、このパラメーターを使用します。 詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)」を参照してください。  
  
 bcp.exe コマンドでは、行ターミネータを 16 進数表記で指定すると、値が 0x00 で切り捨てられます。 たとえば、0x410041 を指定した場合、使用されるのは 0x41 になります。  
  
 *row_term* がハイフン (-) またはスラッシュ (/) で始まる場合は、 **-r** と *row_term* 値の間に空白を入れないでください。  
  
 **-R**  
 通貨、日付、時刻のデータを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に一括コピーする場合に、クライアント コンピューターのロケール設定に定義された地域別設定が使用されます。 既定の設定では、地域別設定は無視されます。  
  
 **-S** _server_name_[ **\\** _instance_name_]  
 接続先となる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。 サーバーを指定しない場合、 **bcp** ユーティリティは、ローカル コンピューター上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続されます。 ネットワーク上のリモート コンピューターまたはローカルの名前付きインスタンスから **bcp** コマンドを実行するときは、このオプションが必要です。 サーバー上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続するには、 *server_name*のみを指定します。 の名前付きインスタンスに接続するに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、 *server_name **_\\_** instance_name*を指定します。  
  
 `-t`*field_term*  
 フィールド ターミネータを指定します。 既定値は **\t** (タブ文字) です。 既定のフィールド ターミネータをオーバーライドする場合、このパラメーターを使用します。 詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)」を参照してください。  
  
 bcp.exe コマンドでは、フィールド ターミネータを 16 進数表記で指定すると、値が 0x00 で切り捨てられます。 たとえば、0x410041 を指定した場合、使用されるのは 0x41 になります。  
  
 *Field_term*がハイフン (-) またはスラッシュ (/) で始まる場合は、 `-t` と*field_term*の値の間に空白を入れないでください。  
  
 **-T**  
 **bcp** ユーティリティが統合セキュリティを使用した信頼関係接続を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に接続することを指定します。 ネットワーク ユーザーのセキュリティ資格情報である *login_id*および *password* は必要ありません。 **-T** を指定しない場合、正常にログインするには **-U** と **-P** を指定する必要があります。  
  
 **-U** _login_id_  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]への接続に使用されるログイン ID を指定します。  
  
> [!IMPORTANT]  
>  **bcp** ユーティリティが、統合セキュリティを使用したセキュリティ接続で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に接続している場合は、 **user name** と *password* の組み合わせではなく、 *-T* オプション (セキュリティ接続) を使用します。  
  
 **-v**  
 **bcp** ユーティリティのバージョン番号と著作権に関する情報を報告します。  
  
 **-V** (**80** | **90** | **100**| **110**)  
 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のデータ型を使用して一括コピー操作を実行します。 このオプションを使用すると、フィールドごとにプロンプトが表示されません。既定値が使用されます。  
  
 **80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]  
  
 **90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] および [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]  
  
 **110 =[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**  
  
 たとえば、 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]でサポートされておらず、それ以降のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]で導入された型のデータを生成する場合は、-V80 オプションを使用します。  
  
 詳細については、「 [以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)」をご覧ください。  
  
 `-w`  
 Unicode 文字を使用して一括コピー操作を実行します。 このオプションでは、フィールドごとにプロンプトは表示されません。`nchar`ストレージ型としてを使用します。プレフィックスなし、フィールド区切り文字**\t** (タブ文字)、および行ターミネータとして**\n** (改行文字) を使用します。 `-w` と `-c` には互換性がありません。  
  
 詳細については、「 [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)」をご覧ください。  
  
 **-x**  
 **format** および **-f**_format_file_ オプションと共に使用し、既定の XML ではないフォーマット ファイルの代わりに XML ベースのフォーマット ファイルを生成します。 **-x** はデータのインポート時とエクスポート時には機能しません。 **format** および **-f**_format_file_ の両方を指定せずに使用すると、エラーが生成されます。  
  
## <a name="remarks"></a>Remarks  
 **Bcp** 12.0 クライアントは、ツールをインストールするときにインストールされ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ます。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] と以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の両方のツールがインストールされている場合、PATH 環境変数の値によっては、**bcp** 12.0 クライアントではなく、以前の **bcp** クライアントを使用している可能性があります。 この環境変数によって Windows で実行可能ファイルを探すときに使用されるディレクトリのセットが定義されます。 使用しているバージョンを確認するには、Windows のコマンド プロンプトで **bcp /v** コマンドを実行します。 コマンド パスを PATH 環境変数で設定する方法の詳細については、Windows のヘルプを参照してください。  
  
 XML フォーマット ファイルは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ツールが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client と共にインストールされている場合のみサポートされます。  
  
 **bcp** ユーティリティのある場所や、実行する方法、コマンド プロンプト ユーティリティの構文規則については、「[コマンド プロンプト ユーティリティ リファレンス &#40;データベース エンジン&#41;](../tools/command-prompt-utility-reference-database-engine.md)」をご覧ください。  
  
 データを一括インポートまたはエクスポート用に準備する方法については、「 [一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)オプションと同時に使う場合はその知識が必要になります。  
  
 一括インポートによって実行される行挿入操作がトランザクション ログに記録される条件について詳しくは、「 [一括インポートで最小ログ記録を行うための前提条件](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」をご覧ください。  
  
## <a name="native-data-file-support"></a>ネイティブ データ ファイルのサポート  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の **bcp** ユーティリティでは、 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]、および [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]と互換性のあるネイティブ データ ファイルがサポートされています。  
  
## <a name="computed-columns-and-timestamp-columns"></a>計算列とタイムスタンプ列  
 計算列または `timestamp` 型列にインポートされるデータ ファイル内の値は無視され、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって自動的に値が割り当てられます。 データ ファイルにテーブル内の計算列または `timestamp` 型列の値が含まれない場合は、フォーマット ファイルを使用して、データのインポート時にテーブル内の計算列または `timestamp` 型列を無視するように指定します。[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、この列に値が自動的に割り当てられます。  
  
 計算列と `timestamp` 型列は、通常どおり、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] からデータ ファイルに一括コピーされます。  
  
## <a name="specifying-identifiers-that-contain-spaces-or-quotation-marks"></a>空白や引用符を含む識別子の指定  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子には、空白や引用符などを埋め込むことができます。 これらの識別子は次のように扱う必要があります。  
  
-   コマンド プロンプトで空白や引用符を含む識別子またはファイル名を指定する場合、識別子を二重引用符 (" ") で囲みます。  
  
     たとえば、次の `bcp out` コマンドでは、 `Currency Types.dat`という名前のデータ ファイルが作成されます。  
  
    ```  
    bcp AdventureWorks2012.Sales.Currency out "Currency Types.dat" -T -c  
    ```  
  
-   空白や引用符を含むデータベース名を指定するには、`-q` オプションを使用する必要があります。  
  
-   空白文字や引用符を含んでいる所有者、テーブル、またはビューの名前については、次のうちのいずれかを行うことができます。  
  
    -   `-q` オプションを指定します。  
  
    -   所有者名、テーブル名、またはビュー名を、引用符内でかっこ ([ ]) を使用して囲みます。  
  
## <a name="data-validation"></a>データ検証  
 **bcp** によってデータ検証とデータ チェックが実行されるようになったため、無効なデータを含むデータ ファイルに対して実行した場合、このスクリプトは失敗する可能性があります。 たとえば、 **bcp** では次の検証が行われます。  
  
-   `float` データ型と `real` データ型のネイティブ表記が有効かどうか。  
  
-   Unicode データが偶数バイト長かどうか。  
  
 以前のリリースでは、クライアントが無効なデータにアクセスを試みるまでは失敗が発生することはありませんでしたが、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で一括インポート可能であった無効な形式のデータが、新しいバージョンでは読み込みに失敗する場合があります。 今回のリリースでは検証機能が追加されたため、一括読み込み後のクエリで発生する問題を最小限に抑えられます。  
  
## <a name="bulk-exporting-or-importing-sqlxml-documents"></a>SQLXML ドキュメントの一括エクスポートまたは一括インポート  
 SQLXML データを一括エクスポートまたは一括インポートする場合、フォーマット ファイルのデータ型には次のいずれかを使用します。  
  
|データ型|結果|  
|---------------|------------|  
|SQLCHAR または SQLVARYCHAR|データは、クライアント コード ページまたは照合順序で暗黙的に指定されるコード ページで送られます。 結果は、フォーマット ファイルを指定せずに、`-c` スイッチを指定した場合と同じです。|  
|SQLNCHAR または SQLNVARCHAR|データは Unicode として送られます。 結果は、フォーマット ファイルを指定せずに、`-w` スイッチを指定した場合と同じです。|  
|SQLBINARY または SQLVARYBIN|データは変換なしで送られます。|  
  
## <a name="permissions"></a>アクセス許可  
 **bcpout** 操作には、ソース テーブルでの SELECT 権限が必要です。  
  
 **bcpin** 操作には、対象となるテーブルでの SELECT/INSERT 権限が最低限必要となります。 また、次のうちのいずれかに該当する場合は、ALTER TABLE 権限が必要です。  
  
-   制約が存在するため、CHECK_CONSTRAINTS ヒントを指定しません。  
  
    > [!NOTE]  
    >  制約の無効化は既定の動作です。 制約を明示的に有効にするには、CHECK_CONSTRAINTS ヒントと共に **-h** オプションを使用します。  
  
-   トリガーが存在するため、FIRE_TRIGGER ヒントを指定しません。  
  
    > [!NOTE]  
    >  既定では、トリガーは起動しません。 トリガーを明示的に起動するには、FIRE_TRIGGERS ヒントと共に **-h** オプションを使用します。  
  
-   **-E** オプションを使用して、データ ファイルから ID 値をインポートします。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]からは、対象テーブルでの ALTER TABLE 権限が必要となりました。 この新しい要件により、対象テーブルでの ALTER TABLE 権限がユーザー アカウントに与えられていないと、トリガーおよび制約チェックを実行しない **bcp** スクリプトは失敗する可能性があります。  
  
## <a name="character-mode--c-and-native-mode--n-best-practices"></a>キャラクター モード (-c) およびネイティブ モード (-n) のベスト プラクティス  
 このセクションでは、キャラクター モード (-c) およびネイティブ モード (-n) の推奨事項について説明します。  
  
-   (管理者/ユーザー) 可能であれば、ネイティブ形式 (-n) を使用して、区切り記号の問題を回避します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を使用してエクスポートおよびインポートを行うには、ネイティブ形式を使用します。 データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以外のデータベースにインポートする場合は、データを[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] からエクスポートするときに -c または -w オプションを使用します。  
  
-   (管理者) BCP OUT を使用するときに、データを検証します。 たとえば、BCP OUT、BCP IN、その後 BCP OUT を使用する場合、データが正しくエクスポートされ、ターミネータ値がデータ値の一部として使用されていないことを確認します。 ターミネータ値とデータ値の競合を回避するために、-t および -r オプションを使用して、既定のターミネータ値をランダムな 16 進数値でオーバーライドすることを検討してください。  
  
-   (ユーザー) 実際の文字列値と競合する可能性を最小限に抑えるために、長くて一意のターミネータ (バイトまたはキャラクターの任意のシーケンス) を使用します。 これには、-t および -r オプションを使用します。  
  
## <a name="examples"></a>例  
 このセクションには、次の例が含まれています。  
  
-   A. データ ファイルへのテーブル行のコピー (セキュリティ接続を使用)  
  
-   B. データ ファイルへのテーブル行のコピー (混合モード認証を使用)  
  
-   C. ファイルからテーブルへのデータのコピー  
  
-   D. データ ファイルへの特定の列のコピー  
  
-   E. データ ファイルへの特定の行のコピー  
  
-   F. クエリからデータ ファイルへのデータのコピー  
  
-   G. XML 以外のフォーマット ファイルの作成  
  
-   H. XML フォーマット ファイルの作成  
  
-   I. フォーマット ファイルを使用した **bcp**での一括インポート  
  
### <a name="a-copying-table-rows-into-a-data-file-with-a-trusted-connection"></a>A. データ ファイルへのテーブル行のコピー (セキュリティ接続を使用)  
 次の例では、 **テーブルに対して** out `AdventureWorks2012.Sales.Currency` オプションを実行します。 `Currency.dat` という名前のデータ ファイルを作成し、文字形式を使用してテーブルのデータをこのデータ ファイルにコピーします。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 コマンド プロンプトで、次のコマンドを入力します。  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -T -c  
```  
  
### <a name="b-copying-table-rows-into-a-data-file-with-mixed-mode-authentication"></a>B. データ ファイルへのテーブル行のコピー (混合モード認証を使用)  
 次の例では、 **テーブルに対して** out `AdventureWorks2012.Sales.Currency` オプションを実行します。 `Currency.dat` という名前のデータ ファイルを作成し、文字形式を使用してテーブルのデータをこのデータ ファイルにコピーします。  
  
 この例では、混合モード認証を使用していることを前提としているため、ログイン ID の指定に **-U** スイッチを使用する必要があります。 また、ローカル コンピューター上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続する以外の場合は、 **-S** スイッチを使用して、システム名と、オプションでインスタンス名を指定します。  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -c -U<login_id> -S<server_name\instance_name>  
```  
  
 システムによってパスワードの入力が求められます。  
  
### <a name="c-copying-data-from-a-file-to-a-table"></a>C. ファイルからテーブルへのデータのコピー  
 次の例では、前の例で作成したファイル (`Currency.dat`) を使用して、**in** オプションを実行します。 ただし、最初に `AdventureWorks2012 Sales.Currency` テーブルの空のコピー、`Sales.Currency2` が作成され、これにデータがコピーされます。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 空のテーブルを作成するには、クエリ エディターで次のコマンドを入力します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO AdventureWorks2012.Sales.Currency2   
FROM AdventureWorks2012.Sales.Currency WHERE 1=2;  
```  
  
 文字データを新規のテーブルに一括コピーする、つまりデータをインポートするには、コマンド プロンプトで次のコマンドを入力します。  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -c  
```  
  
 コマンドが正常終了したことを確認するには、クエリ エディターでテーブルの内容を表示し、次を入力します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM Sales.Currency2  
```  
  
### <a name="d-copying-a-specific-column-into-a-data-file"></a>D. データ ファイルへの特定の列のコピー  
 特定の列をコピーする場合に、 **queryout** オプションを使用できます。 次の例では、 `Name` テーブルの `Sales.Currency` 列のみをデータ ファイルにコピーします。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp "SELECT Name FROM AdventureWorks.Sales.Currency" queryout Currency.Name.dat -T -c  
```  
  
### <a name="e-copying-a-specific-row-into-a-data-file"></a>E. データ ファイルへの特定の行のコピー  
 特定の行をコピーする場合に、 **queryout** オプションを使用できます。 次の例では、`Jarrod Rana` という名前の連絡先の行のみを `AdventureWorks2012.Person.Person` テーブルからデータ ファイル (`Jarrod Rana.dat`) にコピーします。この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp "SELECT * FROM AdventureWorks2012.Person.Person WHERE FirstName='Jarrod' AND LastName='Rana' "  queryout "Jarrod Rana.dat" -T -c  
```  
  
### <a name="f-copying-data-from-a-query-to-a-data-file"></a>F. クエリからデータ ファイルへのデータのコピー  
 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントからデータ ファイルに結果セットをコピーするには、**queryout** オプションを使用します。 次の例では、名前 (姓、名の順) を `AdventureWorks2012.Person.Person` テーブルから、`Contacts.txt` データ ファイルへコピーします。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp "SELECT FirstName, LastName FROM AdventureWorks2012.Person.Person ORDER BY LastName, Firstname" queryout Contacts.txt -c -T  
```  
  
### <a name="g-creating-a-non-xml-format-file"></a>G. XML 以外のフォーマット ファイルの作成  
 次の例では、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース内の `Currency.fmt` テーブルに対して、`Sales.Currency` という名前の XML 以外のフォーマット ファイルを作成します。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c  -f Currency.fmt  
```  
  
 詳細については、「 [XML 以外のフォーマット ファイル &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)でサポートされる従来のフォーマットです。  
  
### <a name="h-creating-an-xml-format-file"></a>H. XML フォーマット ファイルの作成  
 次の例では、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース内の `Currency.xml` テーブルに対して `Sales.Currency` という名前の XML フォーマット ファイルを作成します。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c -x -f Currency.xml  
```  
  
> [!NOTE]  
>  **-x** スイッチを使用するには、 **bcp** 9.0 クライアントを使用している必要があります。 **Bcp** 9.0 クライアントの使用方法の詳細については、「解説」を参照してください。  
  
 詳細については、「 [XML フォーマット ファイル &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)です。  
  
### <a name="i-using-a-format-file-to-bulk-import-with-bcp"></a>I. フォーマット ファイルを使用した bcp での一括インポート  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスにデータをインポートするときに、既に作成してあるフォーマット ファイルを使用するには、 **-f** スイッチを **in** オプションと共に使用します。 たとえば、次のコマンドは、作成済みのフォーマット ファイル (`Currency.dat`) を使用して、データ ファイル (`Sales.Currency`) の内容を `Sales.Currency2` テーブルのコピー (`Currency.xml`) に一括コピーします。 この例では、Windows 認証を使用していること、および **bcp** コマンドを実行しているサーバー インスタンスへのセキュリティ接続があることを前提としています。  
  
 Windows のコマンド プロンプトで、次のように入力します。  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -f Currency.xml  
```  
  
> [!NOTE]  
>  フォーマット ファイルは、データ ファイルのフィールドとテーブル列の数、順序、データ型などが異なる場合に役立ちます。 詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。  
  
## <a name="additional-examples"></a>その他の例  
 次のトピックには、 **bcp**の使用例が含まれています。  
  
-   [フォーマット ファイルの作成 &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)  
  
-   [XML ドキュメントの一括インポートと一括エクスポートの例 &#40;SQL Server&#41;](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [データの一括インポート時の ID 値の保持 &#40;SQL Server&#41;](../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [一括エクスポートまたは一括インポートのデータの準備 &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [SET QUOTED_IDENTIFIER &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [sp_tableoption &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)   
 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
