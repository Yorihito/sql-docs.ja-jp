---
title: パッケージのプロパティを設定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- checkpoints [Integration Services]
- execution properties [Integration Services]
- packages [Integration Services], properties
- identification properties [Integration Services]
- passwords [Integration Services]
- SSIS packages, properties
- transaction properties [Integration Services]
- updating package properties
- forced execution value properties [Integration Services]
- security properties [Integration Services]
- version properties [Integration Services]
- SQL Server Integration Services packages, properties
ms.assetid: 13f81c3e-2b18-4f83-b445-a2f4a2c560aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6d6884bf7a29c259eb943da02b5bb9e06ff330da
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421709"
---
# <a name="set-package-properties"></a>パッケージのプロパティを設定する
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のグラフィカル インターフェイスを使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のパッケージを作成する場合、パッケージ オブジェクトのプロパティは [プロパティ] ウィンドウで設定します。  
  
 **[プロパティ]** ウィンドウでは、プロパティが分類され、アルファベット順で一覧が提供されます。 **[プロパティ]** ウィンドウの表示をカテゴリ別に並べ替えるには、[項目別] アイコンをクリックします。  
  
 カテゴリ別に並べ替えると、 **[プロパティ]** ウィンドウは、プロパティを次のカテゴリにグループ化します。  
  
-   [チェックポイント](#Checkpoints)  
  
-   [実行](#Execution)  
  
-   [強制実行値](#ForcedExecutionValue)  
  
-   [[識別]](#Identification)  
  
-   [その他](#Misc)  
  
-   [セキュリティ](#Security)  
  
-   [トランザクション](#Transactions)  
  
-   [バージョン](#Version)  
  
 **[プロパティ]** ウィンドウで設定できないパッケージの追加プロパティの詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.Package>」を参照してください。  
  
### <a name="to-set-package-properties-in-the-properties-window"></a>[プロパティ] ウィンドウでパッケージのプロパティを設定するには  
  
-   [パッケージのプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-package.md)  
  
## <a name="properties-by-category"></a>カテゴリ別プロパティ  
 次の表は、パッケージのプロパティをカテゴリ別に一覧表示しています。  
  
###  <a name="checkpoints"></a><a name="Checkpoints"></a> チェックポイント  
 このカテゴリのプロパティを使用すると、パッケージ制御フローで障害が発生した時点からパッケージを再開できます。制御フローの最初からパッケージを再実行する必要はありません。 詳細については、「[チェックポイントを使用してパッケージを再開する](packages/restart-packages-by-using-checkpoints.md)」を参照してください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`CheckpointFileName`|パッケージを再開するチェックポイントに関する情報をキャプチャする、ファイルの名前です。 パッケージが正常に完了すると、このファイルは削除されます。|  
|`CheckpointUsage`|パッケージが再開できる時点を指定します。 値は、`Never`、`IfExists`、および `Always` です。 このプロパティの既定値は、パッケージを再起動できないことを示す `Never` です。 詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DTSCheckpointUsage>」を参照してください。|  
|`SaveCheckpoints`|パッケージの実行時にチェックポイントをチェックポイント ファイルに書き込むかどうかを指定します。 このプロパティの既定値は `False` です。|  
  
> [!NOTE]  
>  dtexec の `/CheckPointing on` オプションを使用すると、パッケージの `SaveCheckpoints` プロパティを True に設定した場合、および `CheckpointUsage` プロパティを Always に設定した場合と同等の効果が得られます。 詳細については、「[dtexec ユーティリティ](packages/dtexec-utility.md)」を参照してください。  
  
###  <a name="execution"></a><a name="Execution"></a> の実行  
 このカテゴリのプロパティは、パッケージ オブジェクトの実行時の動作を構成します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`DelayValidation`|パッケージの実行時までパッケージの検証を遅らせるかどうかを示します。 このプロパティの既定値は、`False` です。|  
|**Disable**|パッケージを無効にするかどうかを示します。 このプロパティの既定値は `False` です。|  
|`DisableEventHandlers`|パッケージのイベント ハンドラーを実行するかどうかを示します。 このプロパティの既定値は `False` です。|  
|`FailPackageOnFailure`|パッケージ コンポーネント内でエラーが発生した場合、パッケージが失敗するかどうかを示します。 このプロパティの有効な値は、`False` だけです。|  
|`FailParentOnError`|子コンテナーでエラーが発生した場合、親コンテナーが失敗するかどうかを示します。 このプロパティの既定値は `False` です。|  
|`MaxConcurrentExecutables`|パッケージが同時実行できる実行可能ファイルの数を示します。 このプロパティの既定値は、パッケージを再起動できないことを示す **-1**です。これは、ファイル数に制限がないことを示します。|  
|`MaximumErrorCount`|パッケージが実行を停止するまでに発生が許可される、最大エラー数を示します。 このプロパティの既定値は**1**です。|  
|`PackagePriorityClass`|パッケージ スレッドの Win32 スレッド優先度クラスを示します。 値は、`Default`、`AboveNormal`、`Normal`、`BelowNormal`、および `Idle` です。 このプロパティの既定値は `Default` です。 詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DTSPriorityClass>」を参照してください。|  
  
###  <a name="forced-execution-value"></a><a name="ForcedExecutionValue"></a>強制実行値  
 このカテゴリのプロパティは、パッケージのオプションの実行値を構成します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`ForcedExecutionValue`|ForceExecutionValue がに設定されている場合 `True` 、パッケージが返すオプションの実行値を示す値です。 このプロパティの既定値は **0** です。|  
|`ForcedExecutionValueType`|ForcedExecutionValue のデータ型。 このプロパティの既定値は `Int32` です。|  
|`ForceExecutionValue`|コンテナーのオプションの実行値に特定の値を適用する必要があるかどうかを示すブール値です。 このプロパティの既定値は `False` です。|  
  
###  <a name="identification"></a><a name="Identification"></a>番号  
 このカテゴリのプロパティは、パッケージの一意識別子や名前などの情報を提供します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`CreationDate`|パッケージが作成された日付です。|  
|`CreatorComputerName`|パッケージが作成されたコンピューターの名前です。|  
|`CreatorName`|パッケージの作成者の名前です。|  
|`Description`|パッケージ機能の説明です。|  
|`ID`|パッケージ GUID です。パッケージが作成されるときに割り当てられます。 このプロパティは読み取り専用です。 プロパティの新しい乱数値を生成するには `ID` 、 **\<Generate New ID>** ドロップダウンリストでを選択します。|  
|`Name`|パッケージの名前です。|  
|`PackageType`|パッケージの種類です。 値は、`Default`、`DTSDesigner`、`DTSDesigner100`、`DTSWizard`、`SQLDBMaint`、および `SQLReplication` です。 このプロパティの既定値は `Default` です。 詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType>」を参照してください。|  
  
###  <a name="misc"></a><a name="Misc"></a>その他  
 このカテゴリのプロパティは、パッケージで使用する構成と式にアクセスし、パッケージのロケールとログ モードに関する情報を提供するために使用されます。 詳細については、「 [パッケージでプロパティ式を使用する](expressions/use-property-expressions-in-packages.md)」を参照してください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`Configurations`|パッケージで使用する構成のコレクションです。 パッケージ構成を表示して構成するには、参照ボタン ([. **..])** をクリックします。|  
|`Expressions`|パッケージのプロパティの式を作成するには、参照ボタン ([. **..])** をクリックします。<br /><br /> 注: プロパティウィンドウに記載されているプロパティだけでなく、オブジェクトモデルに含まれるすべてのパッケージプロパティのプロパティ式を作成できます。<br /><br /> 詳細については、「 [パッケージでプロパティ式を使用する](expressions/use-property-expressions-in-packages.md)」を参照してください。<br /><br /> 既存のプロパティの式を表示するには、`Expressions` を展開します。 式を変更および評価するには、式テキストボックスの参照ボタン ([. **..])** をクリックします。|  
|`ForceExecutionResult`|パッケージの実行結果です。 有効値は、`None`、`Success`、`Failure`、および `Completion` です。 このプロパティの既定値は `None` です。 詳細については、「T:Microsoft.SqlServer.Dts.Runtime.DTSForcedExecResult」を参照してください。|  
|`LocaleId`|Microsoft Win32 ロケールです。 このプロパティの既定値は、ローカル コンピューター上のオペレーティング システムのロケールです。|  
|`LoggingMode`|パッケージのログ記録の動作を指定する値です。 値は、`Disabled`、`Enabled`、および `UseParentSetting` です。 このプロパティの既定値は `UseParentSetting` です。 詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>」を参照してください。|  
|`OfflineMode`|パッケージがオフライン モードかどうかを示します。 このプロパティは読み取り専用です。 プロジェクト レベルで設定されます。 通常、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーは、変換元と変換先に関連付けられたメタデータを検証するとき、パッケージで使用される各データ ソースに接続を試みます。 **[SSIS]** メニューの **[オフライン作業]** を有効にすると、パッケージを開く前でも、データ ソースを使用できないときに、接続を試行したり検証エラーが返されたりするのを防ぐことができます。 また、 **[オフライン作業]** を有効にしてデザイナーでの操作を高速化し、パッケージを検証するときだけこのオプションを無効にすることもできます。|  
|`SuppressConfigurationWarnings`|構成によって生成された警告を表示しないかどうかを示します。 このプロパティの既定値は `False` です。|  
|`UpdateObjects`|パッケージに含まれるオブジェクトの新しいバージョンが使用できるようになった場合に、パッケージを更新して、そのオブジェクトの新バージョンを使用するかどうかを示します。 たとえば、このプロパティが `True` に設定されている場合は、一括挿入タスクが含まれるパッケージを更新し、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] が提供する新しいバージョンの一括挿入タスクを使用します。 このプロパティの既定値は `False` です。|  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 このカテゴリのプロパティを使用すると、パッケージの保護レベルが設定されます。 詳しくは、「 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)」をご覧ください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`PackagePassword`|パスワードを必要とするパッケージ保護レベル ( `EncryptSensitiveWithPassword` および) のパスワード `EncryptAllWithPassword` 。|  
|`ProtectionLevel`|パッケージの保護レベルです。 値は、、、、 `DontSaveSensitive` `EncryptSensitiveWithUserKey` `EncryptSensitiveWithPassword` `EncryptAllWithPassword` 、および**serverstorage**です。 このプロパティの既定値は `EncryptSensitiveWithUserKey` です。 詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel>」を参照してください。|  
  
###  <a name="transactions"></a><a name="Transactions"></a>トランザクション  
 このカテゴリのプロパティは、パッケージの分離レベルとトランザクション オプションを構成します。 詳細については、「 [Integration Services のトランザクション](integration-services-transactions.md)」をご覧ください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`IsolationLevel`|パッケージ トランザクションの分離レベルです。  このプロパティの既定値は `Serializable` です。 有効な値は、 <br />`Unspecified`<br />`Chaos`<br />`ReadUncommitted`<br />`ReadCommitted`<br />`RepeatableRead`<br />`Serializable`<br />`Snapshot`.<br /><br /> `IsolationLevel` プロパティは、`TransactionOption` プロパティの値が `Required` の場合にのみ、パッケージ トランザクションに適用されます。<br /><br /> 子コンテナーによって要求された `IsolationLevel` プロパティの値は、以下の場合には無視されます。<br /><br /> 子コンテナーの `TransactionOption` プロパティの値が `Supported` である場合。<br />子コンテナーが親コンテナーのトランザクションに参加する場合。<br /><br /> コンテナーによって要求された `IsolationLevel` プロパティの値は、コンテナーが新しいトランザクションを開始する場合にのみ利用されます。 コンテナーは、次の場合に新しいトランザクションを開始します。<br /><br /> コンテナーの `TransactionOption` プロパティの値が `Required` である場合。<br />親がまだトランザクションを開始していない場合。<br /><br /> <br /><br /> 注: `IsolationLevel` プロパティの値 `Snapshot` は、パッケージ トランザクションと互換性がありません。 したがって、`IsolationLevel` プロパティを使用して、パッケージ トランザクションの分離レベルを `Shapshot` に設定することはできません。 SQL クエリを使用して、パッケージ トランザクションを `Snapshot` に設定してください。 詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」を参照してください。<br /><br /> `IsolationLevel` プロパティの詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>」を参照してください。|  
|`TransactionOption`|パッケージに対するトランザクションの関与を示します。 値は `NotSupported` 、、 `Supported` 、 `Required` です。 このプロパティの既定値は `Supported` です。 詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>」を参照してください。|  
  
###  <a name="version"></a><a name="Version"></a>バージョン  
 このカテゴリのプロパティは、パッケージ オブジェクトのバージョンに関する情報を提供します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`VersionBuild`|パッケージのビルドのバージョン番号です。|  
|`VersionComments`|パッケージのバージョンに関するコメントです。|  
|`VersionGUID`|パッケージのバージョンの GUID です。 このプロパティは読み取り専用です。|  
|`VersionMajor`|パッケージの最新のメジャー バージョン。|  
|`VersionMinor`|パッケージの最新のマイナー バージョン。|  
  
  
