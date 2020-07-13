---
title: プロパティ式における列挙定数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9b03bd26ea45ca175f173e1626c30c6277359e1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428959"
---
# <a name="enumerated-constants-in-property-expressions"></a>プロパティ式における列挙定数
  プロパティ式に列挙子メンバー リストの値が含まれている場合、この式ではメンバーの表示名ではなく、列挙子メンバーの数値を使用する必要があります。 たとえば、式で `LoggingMode` プロパティを設定する場合、表示名 Disabled ではなく、数値 2 を使用する必要があります。  
  
 このトピックでは、プロパティ式でメンバーがよく使用される列挙子の表示名に対応した数値のみを示します。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルには、パッケージをプログラムで構築したり、タスクやデータ フロー コンポーネントなどのカスタム パッケージ要素をコード化する際に使用する列挙子が多数追加されています。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のプロパティ ウィンドウには、パッケージとパッケージ オブジェクトのカスタム プロパティに加えて、パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、およびシーケンス コンテナーで使用できる一連のプロパティが含まれています。 列挙子からの値によって設定される共通プロパティである、、 `ForceExecutionResult` `LoggingMode` `IsolationLevel` 、、およびは、[ `Transaction Option` 共通プロパティ] セクションに一覧表示されます。  
  
 次の各セクションでは、列挙定数について説明します。  
  
 [Package](#Package)  
  
 [Foreach ループ列挙子](#Foreach)  
  
 [タスク](#Tasks)  
  
 [メンテナンス プランのタスク](#MaintenancePlanTasks)  
  
 [Common Properties](#CommonProperties)  
  
##  <a name="package"></a><a name="Package"></a> [パッケージ]  
 次の表は、列挙子からの値を使用して設定する、パッケージのプロパティの表示名とそれに対応する数値を示します。  
  
 `PackageType`列挙体の値を使用してプロパティを設定し `DTSPackageType` ます。  
  
|DTSPackageType の表示名|数値|  
|-------------------------------------|-------------------|  
|Default|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage`列挙体の値を使用してプロパティを設定し `DTSCheckpointUsage` ます。  
  
|DTSCheckpointUsage の表示名|数値|  
|-----------------------------------------|-------------------|  
|なし|0|  
|IfExists|1|  
|Always (常に)|2|  
  
 `PackagePriorityClass`列挙体の値を使用してプロパティを設定し `DTSPriorityClass` ます。  
  
|DTSPriorityClass の表示名|数値|  
|---------------------------------------|-------------------|  
|Default|0|  
|AboveNormal|1|  
|Normal|2|  
|BelowNormal|3|  
|アイドル|4|  
  
 `ProtectionLevel`列挙体の値を使用してプロパティを設定し `DTSProtectionLevel` ます。  
  
|DTSProtectionLevel の表示名|数値|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="precedence-constraints"></a><a name="PrecedenceConstraints"></a> 優先順位制約  
 `EvalOp`列挙体の値を使用してプロパティを設定し `DTSPrecedenceEvalOp` ます。  
  
|DTSPrecedenceEvalOp の表示名|数値|  
|------------------------------------------|-------------------|  
|式|1|  
|制約|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value`列挙体の値を使用してプロパティを設定し `DTSExecResult` ます。  
  
|フレンドリ名|数値|  
|-------------------|-------------------|  
|Success|0|  
|障害|1|  
|Completion|2|  
|Canceled|3|  
  
##  <a name="foreach-loop-enumerators"></a><a name="Foreach"></a> Foreach ループ列挙子  
 Foreach ループには、プロパティ式で設定できるプロパティを含む一連の列挙子があります。  
  
### <a name="foreach-ado-enumerator"></a>Foreach ADO 列挙子  
 `Type`列挙体の値を使用してプロパティを設定し `ADOEnumerationType` ます。  
  
|ADOEnumerationType の表示名|数値|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Foreach Nodelist 列挙子  
 `SourceDocumentType`、 `InnerXPathStringSourceType` 、および **[outerxpathstringsourcetype]** の各プロパティ-列挙の値を使用して設定さ `SourceType` れます。  
  
|SourceType の表示名|数値|  
|---------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
|DirectInput|2|  
  
 `EnumerationType`列挙体の値を使用してプロパティを設定し `EnumerationType` ます。  
  
|EnumerationType の表示名|数値|  
|--------------------------------------|-------------------|  
|ナビゲーター|0|  
|ノード|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType`列挙体の値を使用してプロパティを設定し `InnerElementType` ます。  
  
|InnerElementType の表示名|数値|  
|---------------------------------------|-------------------|  
|ナビゲーター|0|  
|ノード|1|  
|NodeText|2|  
  
##  <a name="tasks"></a><a name="Tasks"></a> 処理手順  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、プロパティ式で設定できるプロパティを含む多くのタスクが含まれています。  
  
### <a name="analysis-services-execute-ddl-task"></a>Analysis Services DDL 実行タスク  
 `SourceType`列挙体の値を使用してプロパティを設定し `DDLSourceType` ます。  
  
|DDLSourceType の表示名|数値|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|[FileConnection]|1|  
|変数|2|  
  
### <a name="bulk-insert-task"></a>一括挿入タスク  
 `DataFileType`列挙体の値を使用してプロパティを設定し `DTSBulkInsert_DataFileType` ます。  
  
|DTSBulkInsert_DataFileType の表示名|数値|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>SQL 実行タスク  
 `ResultSetType`列挙体の値を使用してプロパティを設定し `ResultSetType` ます。  
  
|ResultSetType の表示名|数値|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType`列挙体の値を使用してプロパティを設定し `SqlStatementSourceType` ます。  
  
|SqlStatementSourceType の表示名|数値|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|[FileConnection]|2|  
|変数|3|  
  
### <a name="file-system-task"></a>ファイル システム タスク  
 `Operation`列挙体の値を使用してプロパティを設定し `DTSFileSystemOperation` ます。  
  
|DTSFileSystemOperation の表示名|数値|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes`列挙体の値を使用してプロパティを設定し `DTSFileSystemAttributes` ます。  
  
|DTSFileSystemAttributes の表示名|数値|  
|----------------------------------------------|-------------------|  
|Normal|0|  
|アーカイブ|1|  
|[非表示]|2|  
|ReadOnly|4|  
|システム|8|  
  
### <a name="ftp-task"></a>FTP タスク  
 `Operation`列挙体の値を使用してプロパティを設定し `DTSFTPOp` ます。  
  
|DTSFTPOp の表示名|数値|  
|-------------------------------|-------------------|  
|Send|0|  
|受信|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType`列挙体の値を使用してプロパティを設定し `MQMessageType` ます。  
  
|MQMessageType の表示名|数値|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType`列挙体の値を使用してプロパティを設定し `MQStringMessageCompare` ます。  
  
|MQStringMessageCompare の表示名|数値|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType`列挙体の値を使用してプロパティを設定し `MQType` ます。  
  
|MQType の表示名|数値|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>メール送信タスク  
 `MessageSourceType`列挙体の値を使用してプロパティを設定し `SendMailMessageSourceType` ます。  
  
|SendMailMessageSourceType の表示名|数値|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|[FileConnection]|1|  
|変数|2|  
  
 `Priority`列挙体の値を使用してプロパティを設定し `MailPriority` ます。  
  
|MailPriority の表示名|数値|  
|-----------------------------------|-------------------|  
|高|1|  
|Normal|3|  
|低|5|  
  
### <a name="transfer-database-task"></a>データベース転送タスク  
 `Action`列挙体の値を使用してプロパティを設定し `TransferAction` ます。  
  
|TransferAction の表示名|数値|  
|-------------------------------------|-------------------|  
|コピー|0|  
|[詳細ビュー]|1|  
  
 `Method`列挙体の値を使用してプロパティを設定し `TransferMethod` ます。  
  
|TransferMethod の表示名|数値|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>エラー メッセージ転送タスク  
 `IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-jobs-task"></a>ジョブ転送タスク  
 `IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-logins-task"></a>ログイン転送タスク  
 `IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
 `LoginsToTransfer`列挙体の値を使用してプロパティを設定し `LoginsToTransfer` ます。  
  
|LoginsToTransfer の表示名|数値|  
|---------------------------------------|-------------------|  
|[AllLogins]|0|  
|[SelectedLogins]|1|  
|[AllLoginsFromSelectedDatabases]|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Master ストアド プロシージャ転送タスク  
 `IfObjectExists`列挙体の値を使用してプロパティを設定し `IfObjectExists` ます。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-sql-server-objects-task"></a>SQL Server オブジェクトの転送タスク  
 `ExistingData`列挙体の値を使用してプロパティを設定し `ExistingData` ます。  
  
|ExistingData の表示名|数値|  
|-----------------------------------|-------------------|  
|Replace|0|  
|Append|1|  
  
### <a name="web-service-task"></a>Web サービス タスク  
 `OutputType`列挙体の値を使用してプロパティを設定し `DTSOutputType` ます。  
  
|DTSOutputType の表示名|数値|  
|------------------------------------|-------------------|  
|ファイル|0|  
|変数|1|  
  
### <a name="wmi-data-reader-task"></a>WMI データ リーダー タスク  
 `OverwriteDestination`列挙体の値を使用してプロパティを設定し `OverwriteDestination` ます。  
  
|OverwriteDestination の表示名|数値|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType`列挙体の値を使用してプロパティを設定し `OutputType` ます。  
  
|OutputType の表示名|数値|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType`列挙体の値を使用してプロパティを設定し `DestinationType` ます。  
  
|DestinationType の表示名|数値|  
|--------------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
  
 `WqlQuerySourceType`列挙体の値を使用してプロパティを設定し `QuerySourceType` ます。  
  
|QuerySourceType の表示名|数値|  
|--------------------------------------|-------------------|  
|[FileConnection]|0|  
|DirectInput|1|  
|変数|2|  
  
 WMI イベント監視の `ActionAtEvent` プロパティ-列挙の値を使用して設定さ `ActionAtEvent` れます。  
  
|ActionAtEvent の表示名|数値|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout`列挙体の値を使用してプロパティを設定し `ActionAtTimeout` ます。  
  
|ActionAtTimeout の表示名|数値|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent`列挙体の値を使用してプロパティを設定し `AfterEvent` ます。  
  
|AfterEvent の表示名|数値|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout`列挙体の値を使用してプロパティを設定し `AfterTimeout` ます。  
  
|AfterTimeout の表示名|数値|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType`列挙体の値を使用してプロパティを設定し `QuerySourceType` ます。  
  
|QuerySourceType の表示名|数値|  
|--------------------------------------|-------------------|  
|[FileConnection]|0|  
|DirectInput|1|  
|変数|2|  
  
### <a name="xml-task"></a>XML タスク  
 `OperationType`列挙体の値を使用してプロパティを設定し `DTSXMLOperation` ます。  
  
|DTSXMLOperation の表示名|数値|  
|--------------------------------------|-------------------|  
|検証|0|  
|XSLT (XSLT)|1|  
|[XPath]|2|  
|Merge|3|  
|[Diff]|4|  
|修正プログラム|5|  
  
 `SourceType`、 `SecondOperandType` 、およびの各 `XPathSourceType` プロパティ-列挙の値を使用して設定さ `DTSXMLSourceType` れます。  
  
|DTSXMLSourceType の表示名|数値|  
|---------------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
|DirectInput|2|  
  
 `DestinationType`および**DiffGramDestinationType**プロパティ-列挙の値を使用して設定し `DTSXMLSaveResultTo` ます。  
  
|DTSXMLSaveResultTo の表示名|数値|  
|-----------------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
  
 `ValidationType`列挙体の値を使用してプロパティを設定し `DTSXMLValidationType` ます。  
  
|DTSXMLValidationType の表示名|数値|  
|-------------------------------------------|-------------------|  
|[DTD]|0|  
|[XSD]|1|  
  
 `XPathOperation`列挙体の値を使用してプロパティを設定し `DTSXMLXPathOperation` ます。  
  
|DTSXMLXPathOperation の表示名|数値|  
|-------------------------------------------|-------------------|  
|評価|0|  
|値|1|  
|NodeList|2|  
  
 `DiffOptions`列挙体の値を使用してプロパティを設定し `DTSXMLDiffOptions` ます。 この列挙子の各オプションは相互排他的ではなく、複数を同時に指定することができます。 複数のオプションを使用するには、適用するオプションをコンマ区切りのリストで指定します。  
  
|DTSXMLDiffOptions の表示名|数値|  
|----------------------------------------|-------------------|  
|なし|0|  
|IgnoreChildOrder|1|  
|[IgnoreComments]|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|[IgnoreNamespaces]|16|  
|[IgnorePrefixes]|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm`列挙体の値を使用してプロパティを設定し `DTSXMLDiffAlgorithm` ます。  
  
|DTSXMLDiffAlgorithm の表示名|数値|  
|------------------------------------------|-------------------|  
|Auto|0|  
|速い|1|  
|[詳細]|2|  
  
##  <a name="maintenance-plan-tasks"></a><a name="MaintenancePlanTasks"></a> メンテナンス プランのタスク  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、メンテナンス プランおよび [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ用の SQL Server タスクを実行する一連のタスクが含まれています。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、プログラムによるこれらのタスクの操作がサポートされていません。また、プログラミング リファレンス ドキュメントには、これらのタスクとその列挙子に関する API ドキュメントが含まれていません。  
  
### <a name="all-maintenance-tasks"></a>すべてのメンテナンス タスク  
 すべてのメンテナンス タスクでは、次の列挙子を使用して、指定したプロパティを設定します。  
  
 `DatabaseSelectionType`列挙体の値を使用してプロパティを設定し `DatabaseSelection` ます。  
  
|DatabaseSelection の表示名|数値|  
|----------------------------------------|-------------------|  
|なし|0|  
|All|1|  
|システム|2|  
|User|3|  
|固有|4|  
  
 `TableSelectionType`列挙体の値を使用してプロパティを設定し `TableSelection` ます。  
  
|TableSelection の表示名|数値|  
|-------------------------------------|-------------------|  
|なし|0|  
|All|1|  
|固有|2|  
  
 `ObjectTypeSelection`列挙体の値を使用してプロパティを設定し `ObjectType` ます。  
  
|ObjectType の表示名|数値|  
|---------------------------------|-------------------|  
|テーブル|0|  
|表示|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>データベースのバックアップ タスク  
 `DestinationCreationType`列挙体の値を使用してプロパティを設定し `DestinationType` ます。  
  
|DestinationType の表示名|数値|  
|--------------------------------------|-------------------|  
|Auto|0|  
|マニュアル|1|  
  
 `ExistingBackupsAction`列挙体の値を使用してプロパティを設定し `ActionForExistingBackups` ます。  
  
|ActionForExistingBackups の表示名|数値|  
|-----------------------------------------------|-------------------|  
|Append|0|  
|Overwrite|1|  
  
 `BackupAction`列挙体の値を使用してプロパティを設定し `BackupTaskType` ます。 このプロパティは、タスクで実行されるバックアップの種類を定義する際に、`BackupIsIncremental` プロパティと合わせて使用します。  
  
|BackupTaskType の表示名|数値|  
|-------------------------------------|-------------------|  
|データベース|0|  
|ファイル|1|  
|ログ|2|  
  
 `BackupDevice`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) 列挙の値を使用してプロパティを設定し `DeviceType` ます。  
  
|DeviceType の表示名|数値|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Tape|1|  
|ファイル|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>メンテナンス クリーンアップ タスク  
 `FileTypeSelected`列挙体の値を使用してプロパティを設定し `FileType` ます。  
  
|FileType の表示名|数値|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType`列挙体の値を使用してプロパティを設定し `TimeUnitType` ます。  
  
|TimeUnitType の表示名|数値|  
|-----------------------------------|-------------------|  
|日|0|  
|Week|1|  
|Month|2|  
|年|3|  
  
### <a name="update-statistics-task"></a>統計の更新タスク  
 `UpdateType`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) 列挙の値を使用してプロパティを設定し `StatisticsTarget` ます。  
  
|StatisticsTarget の表示名|数値|  
|---------------------------------------|-------------------|  
|列|1|  
|インデックス|2|  
|All|3|  
  
##  <a name="common-properties"></a><a name="CommonProperties"></a> 共通プロパティ  
 パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、およびシーケンス コンテナーでは、次の列挙子を使用して、指定されたプロパティを設定できます。  
  
 `ForceExecutionResult`列挙体の値を使用してプロパティを設定し `DTSForcedExecResult` ます。  
  
|DTSForcedExecResult の表示名|数値|  
|------------------------------------------|-------------------|  
|なし|-1|  
|Success|0|  
|障害|1|  
|Completion|2|  
  
 `IsolationLevel`プロパティ-.NET Framework 列挙体によって設定さ `IsolationLevel` れます。 詳細については、 [MSDN ライブラリ](https://go.microsoft.com/fwlink?LinkId=17313)の .NET Framework クラス ライブラリを参照してください。  
  
 `LoggingMode`列挙体の値を使用してプロパティを設定し `DTSLoggingMode` ます。  
  
|DTSLoggingMode の表示名|数値|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|有効|1|  
|無効|2|  
  
 `TransactionOption`列挙体の値を使用してプロパティを設定し `DTSTransactionOption` ます。  
  
|DTSTransactionOption の表示名|数値|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|サポートされています|1|  
|必須|2|  
  
## <a name="related-tasks"></a>Related Tasks  
 [プロパティ式を追加または変更する](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>参照  
 [パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md)   
 [Integration Services &#40;SSIS&#41; パッケージ](../integration-services-ssis-packages.md)   
 [Integration Services コンテナー](../control-flow/integration-services-containers.md)   
 [Integration Services タスク](../control-flow/integration-services-tasks.md)   
 [優先順位制約](../control-flow/precedence-constraints.md)  
  
  
