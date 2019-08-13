---
title: sp_estimate_data_compression_savings (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs:
- TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e7d9c1e2f3c6d0de5e41775c445b46f232d5985
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811382"
---
# <a name="sp_estimate_data_compression_savings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  要求されたオブジェクトの現在のサイズ、および要求された圧縮状態での推定オブジェクト サイズを返します。 圧縮は、テーブル全体またはテーブルの一部について評価できます。 これには、ヒープ、クラスター化インデックス、非クラスター化インデックス、列ストアインデックス、インデックス付きビュー、およびテーブルとインデックスのパーティションが含まれます。 オブジェクトは、行、ページ、列ストア、または列ストアアーカイブの圧縮を使用して圧縮できます。 テーブル、インデックス、またはパーティションが既に圧縮されている場合は、このプロシージャを使用して、再圧縮された場合のテーブル、インデックス、またはパーティションのサイズを推定できます。  
  
> [!NOTE]
>  圧縮と**sp_estimate_data_compression_savings**は、のすべての[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 要求された圧縮設定を使用した場合のオブジェクト サイズを推定するために、このストアド プロシージャでは、ソース オブジェクトがサンプリングされ、そのデータが tempdb に作成された同等のテーブルとインデックスに読み込まれます。 さらに、tempdb に作成されたテーブルまたはインデックスが要求された設定に圧縮され、圧縮で削減される推定領域が計算されます。  
  
 テーブル、インデックス、またはパーティションの圧縮状態を変更するには、 [ALTER table](../../t-sql/statements/alter-table-transact-sql.md)ステートメントまたは[alter index](../../t-sql/statements/alter-index-transact-sql.md)ステートメントを使用します。 圧縮に関する一般的な情報については、「[データ圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
> [!NOTE]  
>  既存のデータが断片化されている場合は、インデックスを再構築することで、圧縮を使用しなくてもデータのサイズを削減できる可能性があります。 インデックスについては、再構築中に FILL FACTOR が適用されます。 これによってインデックスのサイズが増える可能性があります。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [@index_id = ] index_id   
   , [@partition_number = ] partition_number   
   , [@data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @schema_name=] '*schema_name*'  
 テーブルまたはインデックス付きビューを含んでいるデータベース スキーマの名前です。 *schema_name*は**sysname**です。 *Schema_name*が NULL の場合は、現在のユーザーの既定のスキーマが使用されます。  
  
 [ @object_name=] '*object_name*'  
 インデックスが有効になっているテーブルまたはインデックス付きビューの名前です。 *object_name* は **sysname** です。  
  
 [ @index_id=] '*index_id*'  
 インデックスの ID です。 *index_id*は**int**,、値は次のいずれかを指定することができます。インデックスの id 番号、NULL、または 0 ( *object_id*がヒープの場合)。 ベース テーブルまたはビューのすべてのインデックスについて情報を返すには、NULL を指定します。 NULL を指定する場合は、 *partition_number*にも null を指定する必要があります。  
  
 [ @partition_number=] '*partition_number*'  
 オブジェクトのパーティション番号です。 *partition_number*は**int**,、値は、インデックスまたはヒープのパーティション番号、NULL、または1、非パーティションのインデックスまたはヒープの値のいずれかを指定することができます。  
  
 パーティションを指定するには、 [$partition](../../t-sql/functions/partition-transact-sql.md)関数を指定することもできます。 所有するオブジェクトのすべてのパーティションについて情報を返すには、NULL を指定します。  
  
 [ @data_compression=] '*data_compression*'  
 評価される圧縮の種類です。 *data_compression*には、次のいずれかの値を指定できます。NONE、ROW、PAGE、列ストア、または COLUMNSTORE_ARCHIVE。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 テーブル、インデックス、またはパーティションの現在のサイズと推定サイズの情報を提供する以下の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|テーブルまたはインデックス付きビューの名前。|  
|schema_name|**sysname**|テーブルまたはインデックス付きビューのスキーマ。|  
|index_id|**int**|インデックスのインデックス ID。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス|  
|partition_number|**int**|パーティション番号。 非パーティション テーブルまたはインデックスの場合は 1 を返します。|  
|size_with_current_compression_setting (KB)|**bigint**|要求されたテーブル、インデックス、またはパーティションの現在のサイズ。|  
|size_with_requested_compression_setting (KB)|**bigint**|要求された圧縮設定を使用するテーブル、インデックス、またはパーティションの推定サイズ。該当する場合は既存の FILL FACTOR を適用し、断片化が生じていないことを前提としています。|  
|sample_size_with_current_compression_setting (KB)|**bigint**|現在の圧縮設定を使用するサンプルのサイズ。 この列には、断片化も含まれます。|  
|sample_size_with_requested_compression_setting (KB)|**bigint**|要求された圧縮設定を使用して作成されたサンプルのサイズ。該当する場合は既存の FILL FACTOR を適用し、断片化は考慮していません。|  
  
## <a name="remarks"></a>コメント  
 Sp_estimate_data_compression_savings を使用して、行、ページ、列ストア、または列ストアアーカイブの圧縮に対してテーブルまたはパーティションを有効にしたときに発生する節約効果を推定します。 たとえば、行の平均サイズを 40% 削減できれば、オブジェクトのサイズを 40% 削減できる可能性があります。 これは FILL FACTOR と行サイズに左右されるため、領域を削減できない場合もあります。 たとえば、長さ 8,000 バイトの行があり、そのサイズを 40% 削減したとしても、データ ページに収まるのは 1 行のみであることに変わりはないので、 領域は削減されません。  
  
 sp_estimate_data_compression_savings を実行してテーブルが増大するという結果が示される場合は、テーブルの多くの行でデータ型の有効桁数がほとんど使用されており、圧縮された形式に必要なわずかなオーバーヘッドが積み重なって、圧縮による削減量を上回ることを意味しています。 このようなまれなケースでは、圧縮を使用しないでください。  
  
 テーブルで圧縮が有効になっている場合は、sp_estimate_data_compression_savings を使用して、テーブルが圧縮されていない場合の平均行サイズを推定します。  
  
 この操作中に、テーブルで (IS) ロックが取得されます。 (IS) ロックを取得できない場合は、プロシージャがブロックされます。 テーブルは、READ COMMITTED 分離レベルでスキャンされます。  
  
 要求された圧縮設定が現在の圧縮設定と同じである場合は、ストアド プロシージャが既存の FILL FACTOR を使用して、データが断片化されていない状態での推定サイズを返します。  
  
 インデックス ID またはパーティション ID が存在しない場合は、結果が返されません。  
  
## <a name="permissions"></a>アクセス許可  
 テーブルに対する SELECT 権限が必要です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 SQL Server 2019 より前では、このプロシージャは列ストアインデックスには適用されませんでした。したがって、データ圧縮パラメーターの列ストアと COLUMNSTORE_ARCHIVE は受け入れられませんでした。  SQL Server 2019 以降では、列ストアインデックスは、推定のソースオブジェクトとしても、要求された圧縮の種類としても使用できます。

## <a name="considerations-for-columnstore-indexes"></a>列ストアインデックスに関する注意点
 SQL Server 2019 以降では、sp_estimate_compression_savings は列ストアと列ストアアーカイブの両方の圧縮の推定をサポートしています。 ページと行の圧縮とは異なり、列ストア圧縮をオブジェクトに適用するには、新しい列ストアインデックスを作成する必要があります。 このため、このプロシージャの列ストアおよび COLUMNSTORE_ARCHIVE オプションを使用する場合、プロシージャに提供されたソースオブジェクトの型によって、圧縮サイズの推定に使用される列ストアインデックスの種類が決まります。 次の表は、 @data_compressionパラメーターが列ストアまたは COLUMNSTORE_ARCHIVE に設定されている場合に、各ソースオブジェクトの種類の圧縮節約量を推定するために使用される参照オブジェクトを示しています。

 |ソースオブジェクト|参照オブジェクト|
 |-----------------|---------------|
 |ヒープ|クラスター化列ストア インデックス|
 |クラスター化インデックス|クラスター化列ストア インデックス|
 |非クラスター化インデックス|非クラスター化列ストアインデックス (キー列と、指定された非クラスター化インデックスの付加列を含む)、およびテーブルのパーティション列 (存在する場合)|
 |非クラスター化列ストア インデックス|非クラスター化列ストアインデックス (提供された非クラスター化列ストアインデックスと同じ列を含む)|
 |クラスター化列ストア インデックス|クラスター化列ストア インデックス|

> [!NOTE]  
> 行ストアのソースオブジェクト (クラスター化インデックス、非クラスター化インデックス、またはヒープ) から列ストア圧縮を推定するときに、列ストアインデックスでサポートされていないデータ型を持つ列がソースオブジェクトに存在する場合、sp_estimate_compression_savingsはエラーで失敗します。

 同様に、 @data_compressionパラメーターが NONE、ROW、PAGE のいずれかに設定され、ソースオブジェクトが列ストアインデックスの場合、使用される参照オブジェクトの概要を次の表に示します。

 |ソースオブジェクト|参照オブジェクト|
 |-----------------|---------------|
 |クラスター化列ストア インデックス|ヒープ|
 |非クラスター化列ストア インデックス|非クラスター化インデックス (キー列として非クラスター化列ストアインデックスに含まれる列と、テーブルのパーティション列 (存在する場合) を付加列として含む)|

> [!NOTE]  
> 列ストアソースオブジェクトから行ストア圧縮 (NONE、ROW、または PAGE) を推定するときに、ソースインデックスに32列を超える列が含まれていないことを確認してください。これは、行ストア (非クラスター化) インデックスでサポートされる制限です。
  
## <a name="examples"></a>使用例  
 次の例では、`Production.WorkOrderRouting` 圧縮を使用して `ROW` テーブルを圧縮した場合のサイズを推定します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [ストアドプロシージャ&#40;のデータベースエンジン transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Unicode 圧縮の実装](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
