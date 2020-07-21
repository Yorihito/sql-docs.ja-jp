---
title: dtexec ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7b6867fa-1039-49b3-90fb-85b84678a612
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45820aa673f31ae9cea7d1f2f4e8b61d63b8670c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423949"
---
# <a name="dtexec-utility"></a>dtexec ユーティリティ
  `dtexec`コマンドプロンプトユーティリティは、パッケージの構成と実行に使用され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。 `dtexec` ユーティリティを使用すると、パラメーター、接続、プロパティ、変数、ログ記録、進行状況インジケーターなど、パッケージの構成と実行に関するすべての機能にアクセスできます。 `dtexec`ユーティリティを使用すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバー、ispac プロジェクトファイル、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージストア、およびファイルシステムからパッケージを読み込むことができます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] に付属するバージョンの `dtexec` ユーティリティを使用して [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] パッケージまたは [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] パッケージを実行すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってパッケージが一時的に [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] にアップグレードされます。 ただし、`dtexec` ユーティリティを使用して、このようなアップグレードによる変更を保存することはできません。 パッケージをに永続的にアップグレードする方法の詳細について [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] は、「 [Integration Services パッケージのアップグレード](../install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
 このトピックのセクションは次のとおりです。  
  
-   [Integration Services サーバーとプロジェクト ファイル](#server)  
  
-   [64 ビット コンピューターでのインストールに関する注意点](#bit)  
  
-   [サイド バイ サイド インストールを使用しているコンピューターに関する注意点](#side)  
  
-   [実行のフェーズ](#phases)  
  
-   [返される終了コード](#exit)  
  
-   [構文規則](#syntaxRules)  
  
-   [xp_cmdshell での dtexec の使用](#cmdshell)  
  
-   [構文](#syntax)  
  
-   [パラメーター](#parameter)  
  
-   [解説](#remark)  
  
-   [使用例](#example)  
  
##  <a name="integration-services-server-and-project-file"></a><a name="server"></a>Integration Services サーバーとプロジェクトファイル  
 を使用して `dtexec` サーバーでパッケージを実行すると [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 、はカタログを `dtexec` 呼び出し[ます。 create_execution &#40;ssisdb データベース&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)、 [catalog. set_execution_parameter_value &#40;ssisdb](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)データベース&#41;および[catalog. start_execution &#40;ssisdb](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)データベース&#41;ストアドプロシージャを実行して、パラメーター値を設定し、実行を開始します。 すべての実行ログは、関連するビューでサーバーから確認できます。また、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で利用可能な標準レポートを使用して確認することもできます。 レポートの詳細については、「 [Integration Services サーバーのレポート](../reports-for-the-integration-services-server.md)」を参照してください。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーでのパッケージの実行例を次に示します。  
  
```  
DTExec /ISSERVER "\SSISDB\folderB\Integration Services Project17\Package.dtsx" /SERVER "." /Envreference 2 /Par "$Project::ProjectParameter(Int32)";1 /Par "Parameter(Int32)";21 /Par "CM.sqlcldb2.SSIS_repro.InitialCatalog";ssisdb /Par "$ServerOption::SYNCHRONIZED(Boolean)";True  
```  
  
 `dtexec` を使用して .ispac プロジェクト ファイルからパッケージを実行する場合の関連オプションは、/Proj[ect] と /Pack[age] です。これらは、プロジェクトのパスとパッケージのストリーム名を指定するために使用されます。 **から** Integration Services プロジェクト変換ウィザード [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を実行してプロジェクトをプロジェクト配置モデルに変換する場合、ウィザードは .ispac プロジェクト ファイルを生成します。 詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../deploy-projects-to-integration-services-server.md)」を参照してください。  
  
 を `dtexec` サードパーティのスケジューリングツールと共に使用して、サーバーに配置されるパッケージのスケジュールを設定でき [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。  
  
##  <a name="installation-considerations-on-64-bit-computers"></a><a name="bit"></a>64ビットコンピューターでのインストールに関する考慮事項  
 64 ビット コンピューターには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって 64 ビット版の `dtexec` ユーティリティ (dtexec.exe) がインストールされます。 特定のパッケージを 32 ビット モードで実行する必要がある場合は、32 ビット版の `dtexec` ユーティリティをインストールする必要があります。 32 ビット版の `dtexec` ユーティリティをインストールするには、セットアップ中に [クライアント ツール] または [[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]] を選択する必要があります。  
  
 既定では、64 ビットと 32 ビットの両方のバージョンの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コマンド プロンプト ユーティリティがインストールされている 64 ビット コンピューターでは、コマンド プロンプトで 32 ビット バージョンが実行されます。 これは、PATH 環境変数で、32 ビット バージョンのディレクトリ パスが 64 ビット バージョンのディレクトリ パスより前に配置されているためです (通常、32ビットのディレクトリパスは、 *\<drive>* Server\110\DTS\Binn files (x86) \MICROSOFT sql ですが、64ビットのディレクトリパスは次のようになっています。 *\<drive>*  
  
> [!NOTE]  
>  SQL Server エージェントを使用してユーティリティを実行する場合は、SQL Server エージェントによって 64 ビット バージョンのユーティリティが自動的に使用されます。 SQL Server エージェントでは、PATH 環境変数ではなくレジストリを使用してユーティリティの適切な実行可能ファイルが特定されます。  
  
 コマンド プロンプトで 64 ビット バージョンのユーティリティが実行されるようにするには、次のいずれかの操作を実行します。  
  
-   コマンドプロンプトウィンドウを開き、64ビットバージョンのユーティリティ (: Server\110\DTS\Binn) が格納されているディレクトリに移動 *\<drive>* し、その場所からユーティリティを実行します。  
  
-   コマンドプロンプトで、64ビットバージョンのユーティリティの完全なパス ( *\<drive>* : Server\110\DTS\Binn) を入力してユーティリティを実行します。  
  
-   PATH 環境変数内のパスの順序を完全に変更するには、64ビットのパス ( *\<drive>* : Server\110\DTS\Binn) を32ビットのパス (:\) の前に配置し *\<drive>* ます。プログラムファイル (x86) \Microsoft SQL Server\110\DTS\Binn) を変数に組み込みます。  
  
##  <a name="considerations-on-computers-with-side-by-side-installations"></a><a name="side"></a>サイドバイサイドインストールを使用したコンピューターに関する考慮事項  
 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] を、[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] または [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] がインストールされているコンピューターにインストールすると、複数のバージョンの `dtexec` ユーティリティがインストールされます。  
  
 正しいバージョンのユーティリティを実行していることを確認するには、コマンドプロンプトで完全なパス ( *\<drive>* SQL Server: \\ \DTS\Binn<version) を入力してユーティリティを実行し \> ます。  
  
##  <a name="phases-of-execution"></a><a name="phases"></a>実行のフェーズ  
 このユーティリティの実行には、4 つのフェーズがあります。 それらのフェーズを次に示します。  
  
1.  コマンド初期フェーズ: コマンド プロンプトによって、指定されたオプションおよび引数のリストが読み取られます。 **/?** オプション または **/HELP** オプションが指定されている場合、後続のフェーズはすべてスキップされます。  
  
2.  パッケージ読み込みフェーズ: `/SQL` 、設定、またはオプション**で指定**されたパッケージ `/DTS` が読み込まれます。  
  
3.  構成フェーズ: 次の順序でオプションが処理されます。  
  
    -   パッケージのフラグ、変数、およびプロパティを設定するオプション  
  
    -   パッケージのバージョン番号およびビルドを確認するオプション  
  
    -   レポートなど、ユーティリティの実行時の動作を構成するオプション  
  
4.  検証および実行フェーズ: パッケージを実行します。 **/VALIDATE** オプションが指定された場合は、実行せずに検証を実行します。  
  
##  <a name="exit-codes-returned"></a><a name="exit"></a>返される終了コード  
 **dtexec ユーティリティから返される終了コード**  
  
 パッケージの実行時、`dtexec` は終了コードを返すことができます。 終了コードは、ERRORLEVEL 変数の値を設定する場合に使用されます。この変数の値は、バッチ ファイル内の条件ステートメントや分岐ロジックでテストできます。 次の表は、終了時に `dtexec` ユーティリティが設定できる値を示しています。  
  
|[値]|説明|  
|-----------|-----------------|  
|0|パッケージが正常に実行されました。|  
|1|パッケージが失敗しました。|  
|3|パッケージはユーザーによって取り消されました。|  
|4|ユーティリティは要求されたパッケージを見つけられません。 パッケージが見つかりませんでした。|  
|5|ユーティリティは要求されたパッケージを読み込めません。 パッケージを読み込めませんでした。|  
|6|ユーティリティは、コマンド ラインに構文の内部エラーまたはセマンティック エラーを検出しました。|  
  
##  <a name="syntax-rules"></a><a name="syntaxRules"></a>構文規則  
 **ユーティリティの構文規則**  
  
 すべてのオプションは、スラッシュ (/) またはマイナス記号 (-) で始まる必要があります。 ここに示すオプションはスラッシュ (/) で始まりますが、マイナス記号 (-) を代わりに使用することもできます。  
  
 引数に空白文字を含めるには、引用符で囲む必要があります。 引数を引用符で囲まないと、空白文字を引数に含めることはできません。  
  
 引用符で囲まれた文字列内に二重引用符がある場合は、単一引用符がエスケープされていることを表します。  
  
 パスワードを除いて、オプションおよび引数では大文字と小文字が区別されません。  
  
##  <a name="using-dtexec-from-the-xp_cmdshell"></a><a name="cmdshell"></a>Xp_cmdshell から dtexec を使用する  
 **xp_cmdshell での dtexec の使用**  
  
 **xp_cmdshell** プロンプトから dtexec を実行できます。 次の例では、UpsertData.dtsx というパッケージを実行し、リターン コードを無視します。  
  
```  
EXEC xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
 次の例では、同じパッケージを実行し、リターン コードを取得します。  
  
```  
DECLARE @returncode int  
EXEC @returncode = xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
> [!IMPORTANT]  
>  では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、新しいインストールでは、 **xp_cmdshell**オプションが既定で無効になっています。 オプションを有効にするには、 **sp_configure** システム ストアド プロシージャを実行します。 詳細については、「 [xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)」を参照してください。  
  
##  <a name="syntax"></a><a name="syntax"></a> 構文  
  
```  
dtexec /option [value] [/option [value]]...  
```  
  
##  <a name="parameters"></a><a name="parameter"></a>パラメータ  
  
-   **/?** [*option_name*]: 省略可能。 コマンド プロンプトのオプション、または指定された *option_name* のヘルプを表示して、ユーティリティを終了します。  
  
     *Option_name*引数を指定した場合、は `dtexec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンラインブックを開始し、dtexec ユーティリティのトピックを表示します。  
  
-   **/Ca [llerInfo]**:   
                  省略可能。 パッケージ実行の追加情報を指定します。 SQL Server エージェントを使用してパッケージを実行する場合、エージェントはこの引数を設定して、パッケージ実行が SQL Server エージェントによって呼び出されることを示します。 `dtexec` ユーティリティがコマンド ラインから実行される場合、このパラメーターは無視されます。  
  
-   **/CheckF[ile]** _filespec_:   
                  省略可能。 Filespec の `CheckpointFileName` パスとファイル spemandcified にパッケージのプロパティを設定し*filespec*ます。 このファイルは、パッケージが再起動されたときに使用されます。 このオプションが指定されていて、ファイル名の値が指定されていない場合、パッケージの `CheckpointFileName` には空の文字列が設定されます。 このオプションが指定されない場合、パッケージの値は保持されます。  
  
-   **/CheckP [ointing]** _{on\ off}_:   
                  省略可能。 パッケージの実行時にパッケージがチェックポイントを使用するかどうかを決定する値を設定します。 値 **on** を指定すると、失敗したパッケージが再実行されます。 失敗したパッケージが再実行される場合、ランタイム エンジンは、障害点からパッケージを再起動するためにチェックポイント ファイルを使用します。  
  
     オプションが値なしで宣言されている場合、既定値は on です。 値が on に設定されていて、チェックポイント ファイルが見つからない場合、パッケージの実行は失敗します。 このオプションが指定されない場合、パッケージの値セットは保持されます。 詳細については、「 [Restart Packages by Using Checkpoints](restart-packages-by-using-checkpoints.md)」を参照してください。  
  
     Dtexec のチェック**ポイント**オプションは、 `SaveCheckpoints` パッケージのプロパティを True に設定し、プロパティを常にに設定することと同じです `CheckpointUsage` 。  
  
-   **/Com[mandFile]** _filespec_:   
                  (省略可能)。 `dtexec` で実行するコマンド オプションを指定します。 *filespec* で指定されたファイルが開き、ファイルに EOF が見つかるまでそのファイルからオプションを読み取ります。 *filespec* は、テキスト ファイルです。 *filespec* 引数には、パッケージの実行に関連付けるコマンド ファイルのファイル名とパスを指定します。  
  
-   **/Conf [igFile]** _filespec_: 省略可能。 値を抽出する構成ファイルを指定します。 このオプションを使用すると、パッケージのデザイン時に指定された構成と異なる実行時構成を設定できます。 パッケージを実行するには、XML 構成ファイルに異なる構成設定を格納してから、 **/ConfigFile** オプションを使用して設定を読み込む必要があります。  
  
     **/ConfigFile** オプションを使用すると、デザイン時に指定しなかった追加の構成を実行時に読み込むことができますが、 **/ConfigFile** オプションを使用しても、デザイン時に指定した構成値を置き換えることはできません。 パッケージ構成が適用されるしくみについては、「 [Package Configurations](../package-configurations.md)」を参照してください。  
  
-   **/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:   
                  省略可能。 指定した名前または GUID の接続マネージャーがパッケージ内にあり、接続文字列が指定されていることを示します。  
  
     このオプションでは、接続マネージャーの名前または GUID を指定する *id_or_name* 引数と、有効な接続文字列を指定する *connection_string* 引数の両方のパラメーターが必須です。 詳細については、「[Integration Services (SSIS) の接続](../connection-manager/integration-services-ssis-connections.md)」を参照してください。  
  
     実行時に **/Connection** オプションを使用すると、デザイン時に指定した場所とは別の場所からパッケージ構成を読み込むことができます。 デザイン時に指定した値は、それらの構成の値で置き換えられます。 ただし、 **/Connection** オプションを使用できるのは、接続マネージャーを使用する構成 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成など) だけです。 パッケージ構成の適用方法については、「[パッケージの構成](../package-configurations.md)と[動作の変更」を参照して SQL Server 2014 の Integration Services 機能を](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)確認してください。  
  
-   **/短所 [oleLog]** [*displayoptions*]; [*list_options*;*src_name_or_guid*]...]: 省略可能。 パッケージの実行中に、指定されたログ エントリをコンソールに表示します。 このオプションを省略した場合、ログ エントリはコンソールに表示されません。 表示を制限するパラメーターなしでオプションが指定された場合、すべてのログ エントリが表示されます。 コンソールに表示されるエントリを制限するには、 *displayoptions* パラメーターを使用して表示する列を指定し、 *list_options* パラメーターを使用してログ エントリの種類を制限します。  
  
    > [!NOTE]  
    >  パラメーターを使用してサーバーでパッケージを実行すると [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `/ISSERVER` 、コンソールの出力が制限され、 **[olelog]** オプションのほとんどは適用できません。 すべての実行ログは、関連するビューでサーバーから確認できます。また、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で利用可能な標準レポートを使用して確認することもできます。 レポートの詳細については、「 [Integration Services サーバーのレポート](../reports-for-the-integration-services-server.md)」を参照してください。  
  
     *displayoptions* の値は次のとおりです。  
  
    -   N (名前)  
  
    -   C (コンピューター)  
  
    -   O (オペレーター)  
  
    -   S (変換元の名前)  
  
    -   G (変換元の GUID)  
  
    -   X (実行 GUID)  
  
    -   M (メッセージ)  
  
    -   T (開始時刻および終了時刻)  
  
     *list_options* の値は次のとおりです。  
  
    -   *I* - 包含一覧を指定します。 指定された変換元の名または変換元の GUID のみがログに記録されます。  
  
    -   *E* - 除外一覧を指定します。 指定された変換元の名前または変換元の GUID はログに記録されません。  
  
    -   *src_name_or_guid* パラメーターには、含めるまたは除外するイベント名、変換元の名前、変換元の GUID を指定します。  
  
     同じコマンドプロンプトで複数の **/consolelog**オプションを使用すると、次のように対話します。  
  
    -   表示の順序には影響しません。  
  
    -   包含一覧がコマンド ラインに指定されていない場合、すべての種類のログ エントリに対して除外一覧が適用されます。  
  
    -   包含一覧がコマンド ラインに指定されている場合、すべての包含一覧の集合に対して除外一覧が適用されます。  
  
     **/Consolelog**オプションの例については、「**解説**」を参照してください。  
  
-   **/D[ts]** _package_path_:   
                  省略可能。 SSIS パッケージ ストアからパッケージを読み込みます。 SSIS パッケージ ストアに格納されているパッケージは、従来のパッケージ配置モデルを使用して配置されます。 プロジェクト配置モデルを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージを実行するには、`/ISServer` オプションを使用します。 パッケージとプロジェクトの配置モデルの詳細については、「 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。  
  
     *package_path* 引数には、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの相対パスを指定します。このパスは SSIS パッケージ ストアのルートから始まり、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの名前を含むパスです。 *package_path* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *package_path* 引数を引用符で囲む必要があります。  
  
     `/DTS` オプションは、`/File` または `/SQL` オプションと共に使用することはできません。 複数のオプションが指定された場合、`dtexec` は失敗します。  
  
-   **/De [crypt]**  _password_: 省略可能。 パスワードが暗号化されているパッケージを読み込むときに使用する暗号化解除用パスワードを設定します。  
  
-   **/Dump** _error code_:  
                  省略可能にすると、パッケージの実行中に1つ以上の指定したイベントが発生したときに、デバッグダンプファイル (mdmp と .tmp) が作成されます。 *エラーコード*の引数には、システムによるデバッグダンプファイルの作成をトリガーするイベントコードの種類 (エラー、警告、または情報) を指定します。 イベント コードを複数指定するには、各 *error code* 引数をセミコロン (;) で区切ります。 *error code* 引数に引用符を含めないでください。  
  
     次の例では、DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER のエラーが発生したときにデバッグ ダンプ ファイルが生成されます。  
  
    ```  
    /Dump 0xC020801C  
    ```  
  
     既定では、は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デバッグダンプファイルを次のフォルダーに格納し *\<drive>* ます。  
  
    > [!NOTE]  
    >  デバッグ ダンプ ファイルには機密情報が含まれている場合があります。 アクセス制御リスト (ACL) を使用してファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーしてください。 たとえば、デバッグ ファイルを Microsoft サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。  
  
     このオプションをユーティリティで実行されるすべてのパッケージに適用するには `dtexec` 、 **Dumponcodes** REG_SZ 値を HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL server\110\ssis\setup\dtspath に追加レジストリキーに追加します。 **DumpOnCodes** のデータ値では、システムによるデバッグ ダンプ ファイル作成のトリガーとなるエラー コードを指定します。 複数のエラー コードは、セミコロン (;) で区切る必要があります。  
  
     **DumpOnCodes** 値をレジストリ キーに追加し、 **/Dump** オプションも使用した場合、両方の設定に基づくデバッグ ダンプ ファイルが作成されます。  
  
     デバッグ ダンプ ファイルの詳細については、「 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)」を参照してください。  
  
-   **/Dumponerror**:   
                  省略可能。 パッケージの実行中にエラーが発生した場合に、デバッグダンプファイル (mdmp と .tmp) を作成します。  
  
     既定では、は、デバッグダンプファイルをフォルダーに保存します。このフォルダーには、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] *\<drive>*  
  
    > [!NOTE]  
    >  デバッグ ダンプ ファイルには機密情報が含まれている場合があります。 アクセス制御リスト (ACL) を使用してファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーしてください。 たとえば、デバッグ ファイルを Microsoft サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。  
  
     このオプションをユーティリティで実行されるすべてのパッケージに適用するには、 `dtexec` **dumponerror** REG_DWORD 値を HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL server\110\ssis\setup\dtspath に追加レジストリキーに追加します。 **Dumponerror** REG_DWORD 値の値によって、ユーティリティで **/dumponerror**オプションを使用する必要があるかどうかが決まり `dtexec` ます。  
  
    -   0以外のデータ値は、ユーティリティで **/dumponerror**オプションを使用するかどうかに関係なく、エラーが発生したときにデバッグダンプファイルが作成されることを示し `dtexec` ます。  
  
    -   データ値が0の場合は、ユーティリティで **/dumponerror**オプションを使用しない限り、デバッグダンプファイルは作成されません `dtexec` 。  
  
     デバッグ ダンプ ファイルの詳細については、「 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)」を参照してください。  
  
-   `/Env[Reference]`*環境の参照 ID*:   
                  省略可能。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するパッケージ用に、パッケージ実行で使用される環境参照 (ID) を指定します。 このパラメーターを変数にバインドするように構成すると、環境に含まれる変数の値が使用されます。  
  
     `/Env[Reference]` オプションは、`/ISServer` オプションおよび `/Server` オプションと共に使用します。  
  
     このパラメーターは SQL Server エージェントによって使用されます。  
  
-   **/F[ile]** _filespec_:   
                  省略可能。 ファイル システムに保存されているパッケージを読み込みます。 ファイル システムに保存されているパッケージは、従来のパッケージ配置モデルを使用して配置されます。 プロジェクト配置モデルを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージを実行するには、`/ISServer` オプションを使用します。 パッケージとプロジェクトの配置モデルの詳細については、「[プロジェクトとパッケージの配置](deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。  
  
     *filespec* 引数には、パッケージのパスとファイル名を指定します。 汎用名前付け規則 (UNC) 形式のパス、またはローカル パスのどちらかでパスを指定できます。 *filespec* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *filespec* 引数を引用符で囲む必要があります。  
  
     `/File` オプションは、`/DTS` または `/SQL` オプションと共に使用することはできません。 複数のオプションが指定された場合、`dtexec` は失敗します。  
  
-   **/H [elp]** [*Option_name*]: 省略可能。 オプションのヘルプ、または指定された *option_name* のヘルプを表示して、ユーティリティを終了します。  
  
     *Option_name*引数を指定した場合、は `dtexec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンラインブックを開始し、dtexec ユーティリティのトピックを表示します。  
  
-   `/ISServer`*packagepath*:  
                  省略可能。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するパッケージを実行します。 *PackagePath* 引数には、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するパッケージの完全なパスとファイル名を指定します。 *PackagePath*引数に指定されたパスまたはファイル名にスペースが含まれている場合は、 *PackagePath*引数を引用符で囲む必要があります。  
  
     パッケージ形式は次のとおりです。  
  
    ```  
    \<catalog name>\<folder name>\<project name>\package file name  
    ```  
  
     `/Server` オプションは、`/ISSERVER` オプションと共に使用します。 SSIS サーバーでパッケージを実行できるのは Windows 認証のみです。 現在の Windows ユーザーはパッケージへのアクセスに使用されます。 /Server オプションを省略した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のローカル インスタンスが使用されます。  
  
     `/ISSERVER` オプションを、`/DTS`、`/SQL`、または `/File` の各オプションと共に使用することはできません。 複数のオプションが指定された場合、dtexec は失敗します。  
  
     このパラメーターは SQL Server エージェントによって使用されます。  
  
-   **/L[ogger]** _classid_orprogid;configstring_:  
                  省略可能。 1 つまたは複数のログ プロバイダーを [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行と関連付けます。 *classid_orprogid* パラメーターには、ログ プロバイダーを指定します。指定できるのはクラス GUID です。 *configstring* は、ログ プロバイダーを構成するために使用する文字列です。  
  
     使用できるログ プロバイダーは次のとおりです。  
  
    -   テキスト ファイル:  
  
        -   ProgID: DTS.LogProviderTextFile.1  
  
        -   ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}  
  
    -   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]:  
  
        -   ProgID: DTS.LogProviderSQLProfiler.1  
  
        -   ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
        -   ProgID: DTS.LogProviderSQLServer.1  
  
        -   ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}  
  
    -   Windows イベント ログ:  
  
        -   ProgID: DTS.LogProviderEventLog.1  
  
        -   ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}  
  
    -   XML ファイル:  
  
        -   ProgID: DTS.LogProviderXMLFile.1  
  
        -   ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}  
  
-   **/M[axConcurrent]** _concurrent_executables_:  
                  省略可能。 パッケージが同時に実行できる実行可能ファイルの数を指定します。 負以外の整数または -1 を指定する必要があります。 値 -1 は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] が同時に実行できる実行可能ファイルの最大数が、パッケージを実行するコンピューターのプロセッサの合計数に 2 を加えたものと等しいことを意味します。  
  
-   **/Pack[age]** _PackageName_:  
                  省略可能。 実行されるパッケージを指定します。 このパラメーターは、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]からパッケージを実行する場合に主に使用されます。  
  
-   **/P [assword]** _パスワード_:  
                  省略可能。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証によって保護されているパッケージの取得を可能にします。 このオプションは、 **/User** オプションと共に使用します。 **/Password** オプションを省略して **/User** オプションを使用する場合、空白のパスワードが使用されます。 *password* 値は引用符で囲むことができます。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   **/Par [ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)];*literal_value*: 省略可能。 パラメーター値を指定します。 複数の **/Parameter** オプションを指定できます。 データ型は、文字列としての CLR TypeCodes です。 文字列型でないパラメーターの場合、データ型をかっこで囲んで指定してから、続けてパラメーター名を指定します。  
  
     **/パラメーター**オプションは、オプションと共にのみ使用でき `/ISServer` ます。  
  
     パッケージ パラメーター、プロジェクト パラメーター、およびサーバー オプション パラメーターを示すには、$Package、$Project、$ServerOption の各プレフィックスをそれぞれ使用します。 既定のパラメーターの型はパッケージです。  
  
     パッケージを実行して、プロジェクト パラメーター (myparam) に myvalue を指定し、パッケージ パラメーター (anotherparam) に整数値 12 を指定する例を次に示します。  
  
     `Dtexec /isserver "SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "." /parameter $Project::myparam;myvalue /parameter anotherparam(int32);12`  
  
     パラメーターを使用して、接続マネージャーのプロパティを設定することもできます。 接続マネージャーのパラメーターであることを示すには、CM プレフィックスを使用します。  
  
     次の例では、SourceServer 接続マネージャーの InitialCatalog プロパティが `ssisdb`に設定されています。  
  
    ```  
    /parameter CM.SourceServer.InitialCatalog;ssisdb  
    ```  
  
     次の例では、SourceServer 接続マネージャーの ServerName プロパティが、ローカル サーバーを示すためにピリオド (.) に設定されています。  
  
    ```  
    /parameter CM.SourceServer.ServerName;.  
    ```  
  
-   **/Proj[ect]** _ProjectFile_:  
                  省略可能。 実行されるパッケージの取得元となるプロジェクトを指定します。 *ProjectFile* 引数には、.ispac ファイル名を指定します。 このパラメーターは、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]からパッケージを実行する場合に主に使用されます。  
  
-   **/Rem** _comment_:  
                  省略可能。 コマンド プロンプトまたはコマンド ファイルにコメントを含めます。 引数は省略可能です。 *comment* の値は、引用符で囲むか、空白を含まない文字列を指定する必要があります。 引数を指定しない場合、空白行が挿入されます。 *comment* の値はコマンド初期フェーズで破棄されます。  
  
-   **/Rep [orting]** _level_ [*; event_guid_or_name*[*; event_guid_or_name*[...]]: 省略可能です。 レポートするメッセージの種類を指定します。 *level* に使用できるレポート オプションは次のとおりです。  
  
     **N** レポートしません。  
  
     `E`エラーが報告されます。  
  
     **W** 警告がレポートされます。  
  
     `I`情報メッセージが報告されます。  
  
     **C** カスタム イベントがレポートされます。  
  
     **D** データ フロー タスク イベントがレポートされます。  
  
     **P** 進行状況がレポートされます。  
  
     **V** 詳細がレポートされます。  
  
     V および N の引数は、他のすべての引数と同時には使用できないため、単独で指定する必要があります。 **/レポート**オプションが指定されていない場合、既定のレベルは `E` (エラー)、 **W** (警告)、および**P** (進行状況) になります。  
  
     すべてのイベントの先頭には、"YY/MM/DD HH:MM:SS" の形式のタイムスタンプが付きます。また使用可能な場合は、GUID または表示名も付加されます。  
  
     省略可能なパラメーターの *event_guid_or_name* には、ログ プロバイダーに関する例外のリストを指定します。 この例外で指定されるイベントは、ログに記録されません。指定されないイベントがログに記録されます。  
  
     既定でログに記録されないイベントは、除外する必要はありません。  
  
-   **/Res [t)]** {*deny | Force | ifpossible ら*れます}: 省略可能です。 パッケージの <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティの新しい値を指定します。 パラメーターの意味は次のとおりです。  
  
     *deny* ： <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>」を参照してください。  
  
     *force* ： <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>」を参照してください。  
  
     *ifPossible* ： <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>」を参照してください。  
  
     値が指定されない場合は、既定値の **force** が使用されます。  
  
-   **/Set** [$Sensitive::]*propertyPath; 値*: 省略可能。 パッケージ内のパラメーター、変数、プロパティ、コンテナー、ログ プロバイダー、Foreach 列挙子、または接続の構成をオーバーライドします。 このオプションを指定すると、 **/Set** は *propertyPath* 引数を、指定された値に変更します。 複数の **/Set** オプションを指定できます。  
  
     **/Set**オプションを **/f [** with the] オプションと共に使用することに加えて、 **/set**オプションをオプションまたはオプションと共に使用することもでき `/ISServer` `/Project` ます。 **/Set**をと共に使用すると、/set によって `/Project` パラメーター値が設定されます。 **/Set** **/Set**をと共に使用すると、/set によって `/ISServer` プロパティのオーバーライドが設定されます。 **/Set** さらに、 **/set**をと共に使用すると、 `/ISServer` オプションの $Sensitive プレフィックスを使用して、プロパティをサーバーで機微な値として扱う必要があることを示すことができ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。  
  
     パッケージ構成ウィザードを実行して、 *propertyPath* の値を確認できます。 最後の **[ウィザードの完了]** ページに選択したアイテムのパスが表示されるので、これをコピーして貼り付けることができます。 この操作のみが目的でウィザードを使用した場合は、パスをコピーした後、ウィザードを取り消してください。  
  
     ファイル システムに保存されているパッケージを実行して、変数に新しい値を指定する例を次に示します。  
  
     `dtexec /f mypackage.dtsx /set \package.variables[myvariable].Value;myvalue`  
  
     .ispac プロジェクト ファイルからパッケージを実行して、パッケージとプロジェクトのパラメーターを指定する例を次に示します。  
  
     `/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1`  
  
     **/Set** オプションを使用すると、パッケージ構成を読み込む場所を変更することができます。 ただし、**/Set** オプションを使用しても、デザイン時の構成で指定した値をオーバーライドすることはできません。 パッケージ構成の適用方法については、「[パッケージの構成](../package-configurations.md)と[動作の変更」を参照して SQL Server 2014 の Integration Services 機能を](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)確認してください。  
  
-   `/Ser[ver]`*サーバー*:  
                  省略可能。 `/SQL` オプションまたは `/DTS` オプションが指定されている場合、このオプションにはパッケージを取得するサーバーの名前を指定します。 `/Server` オプションを省略して `/SQL` または `/DTS` オプションを指定した場合、ローカル サーバーに対してパッケージの実行が試行されます。 *server_instance* 値は引用符で囲むことができます。  
  
     `/Ser[ver]` オプションが指定されている場合、`/ISServer` オプションは必須です。  
  
-   **/SQ[L]** _package_path_:  
                  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `msdb` データベースに格納されているパッケージを読み込みます。 `msdb` データベースに格納されているパッケージは、パッケージ配置モデルを使用して配置されます。 プロジェクト配置モデルを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージを実行するには、`/ISServer` オプションを使用します。 パッケージとプロジェクトの配置モデルの詳細については、「 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。  
  
     *package_path* 引数には、取得するパッケージの名前を指定します。 パス名を指定する場合、パス内のフォルダーの最後には円記号 ("\\") を指定します。 *Package_path* 値は引用符で囲むことができます。 *package_path* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *package_path* 引数を引用符で囲む必要があります。  
  
     **/User**、 **/password**、およびオプションをオプションと共に使用でき `/Server` `/SQL` ます。  
  
     **/User** オプションを省略した場合、パッケージへのアクセスに Windows 認証が使用されます。 **/User** オプションを使用する場合、指定する **/User** ログイン名は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証に関連付けられます。  
  
     **/Password** オプションは、 **/User** オプションと共に使用する必要があります。 **/Password** オプションを使用する場合、パッケージは指定されたユーザー名とパスワード情報を使用してアクセスされます。 **/Password** オプションを省略した場合、空白のパスワードが使用されます。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
     `/Server` オプションを省略した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のローカル インスタンスが使用されます。  
  
     `/SQL` オプションは、`/DTS` または `/File` オプションと共に使用することはできません。 複数のオプションが指定された場合、`dtexec` は失敗します。  
  
-   **/Su [m]**: 省略可能。 後続のコンポーネントが受け取る行数を示す増分カウンターを表示します。  
  
-   **/U [ser]** _user_name_:  
                  省略可能。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証によって保護されているパッケージの取得を可能にします。 このオプションは、`/SQL` オプションが指定されている場合にのみ使用されます。 *User_name* 値は引用符で囲むことができます。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   **/Va [lidate]**:  
                  省略可能。 検証フェーズ後、パッケージの実行を停止します。パッケージは実際には実行されません。 検証中に、 **/WarnAsError**オプションを使用すると、は `dtexec` 警告をエラーとして処理するため、検証中に警告が発生した場合、パッケージは失敗します。  
  
-   **/Verifyb [u)]** _major_[*; minor*[*; build*]]: 省略可能。 検証フェーズ中に、パッケージのビルド番号を、 *major*、 *minor*、および *build* 引数に指定されたビルド番号に対して検証します。 不一致が発生した場合、パッケージは実行されません。  
  
     値は長整数型です。 引数は次の 3 つの形式のいずれかになります。 *major* の値は必須です。  
  
    -   *部分*  
  
    -   *major*;*マイナー*  
  
    -   *major*; *minor*; *build*  
  
-   **/VerifyP[ackageID]** _packageID_:  
                  省略可能。 実行するパッケージの GUID を、 *package_id* 引数に指定された値と比較して検証します。  
  
-   **/VerifyS[igned]**:  
                  省略可能。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] でパッケージのデジタル署名を確認します。 パッケージが署名されていないか、署名が有効でない場合、パッケージは失敗します。 詳細については、「 [デジタル署名を使用してパッケージのソースを特定する](../security/identify-the-source-of-packages-with-digital-signatures.md)」を参照してください。  
  
    > [!IMPORTANT]  
    >  パッケージの署名を確認するように構成した場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって確認されるのは、デジタル署名が存在するかどうか、有効かどうか、および信頼関係のある発行元の署名であるかどうかのみです。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、パッケージが変更されたかどうかは確認されません。  
  
    > [!NOTE]  
    >  オプションの**BlockedSignatureStates**レジストリ値で [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] は、またはコマンドラインで設定されたデジタル署名オプションよりも制限が厳しい設定を指定でき `dtexec` ます。 この場合、制限が厳しい方のレジストリ設定が他の設定をオーバーライドします。  
  
-   **/Verifyv [Er、id]** _versionID_: 省略可能。 パッケージの検証フェーズ中に、実行されるパッケージのバージョン GUID を *version_id* 引数に指定された値と比較して検証します。  
  
-   **/VLog** _[Filespec]_: 省略可能。 すべての Integration Services パッケージ イベントを、パッケージの設計時に有効にしたログ プロバイダーに書き込みます。 Integration Services でテキスト ファイルのログ プロバイダーを有効にし、指定したテキスト ファイルにログ イベントを書き込むには、パスとファイル名を *Filespec* パラメーターとして含めます。  
  
     *Filespec* パラメーターを含めない場合、Integration Services でテキスト ファイルのログ プロバイダーが有効になりません。 Integration Services では、パッケージの設計時に有効にしたログ プロバイダーに対してのみ、ログ イベントが書き込まれます。  
  
-   **/W [arnAsError]**:  
                  省略可能。 パッケージは警告をエラーと判断するので、検証中に警告が発生した場合にはパッケージが失敗します。 検証中に警告が発生せず、 **/Validate** オプションが指定されていない場合、パッケージは実行されます。  
  
-   **/X86**: 省略可能。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは 64 ビット コンピューター上で 32 ビット モードでパッケージを実行します。 このオプションは、次に示す条件が満たされた場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって設定されます。  
  
    -   ジョブ ステップの種類が **[SQL Server Integration Services パッケージ]** であること。  
  
    -   **[新しいジョブ ステップ]** ダイアログ ボックスの **[実行オプション]** タブで **[32 ビット ランタイムを使用]** オプションが選択されていること。  
  
     このオプションは、ストアド プロシージャまたは SQL Server 管理オブジェクト (SMO) を使用してジョブをプログラムにより作成することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップに設定することもできます。  
  
     このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのみに使用されます。 コマンド プロンプトで `dtexec` ユーティリティを実行している場合、このオプションは無視されます。  
  
##  <a name="remarks"></a><a name="remark"></a> 解説  
 コマンド オプションの指定順序は、パッケージの実行方法に影響します。  
  
-   オプションは、コマンド ライン上で指定されている順に処理されます。 コマンド ファイルは、コマンド ラインで指定されているとおりに読み取られます。 コマンド ファイル内のコマンドも指定されている順に処理されます。  
  
-   同じオプション、パラメーター、または変数が、同じコマンド ライン ステートメントに複数指定されている場合は、最後に指定されているものが優先されます。  
  
-   **/Set** オプションと **/ConfigFile** オプションは、指定されている順に処理されます。  
  
##  <a name="examples"></a><a name="example"></a> 使用例  
 次の例では、 `dtexec` コマンドプロンプトユーティリティを使用してパッケージを構成および実行する方法を示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。  
  
 **パッケージの実行**  
  
 Windows 認証を使用する [!INCLUDE[ssIS](../../includes/ssis-md.md)] に保存されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを実行するには、次のコードを使用します。  
  
```  
dtexec /sq pkgOne /ser productionServer  
```  
  
 SSIS パッケージ ストアの [ファイル システム] フォルダーに保存されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを実行するには、次のコードを使用します。  
  
```  
dtexec /dts "\File System\MyPackage"  
```  
  
 Windows 認証が使用されていて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に保存されているパッケージを実行せずに検証するには、次のコードを使用します。  
  
```  
dtexec /sq pkgOne /ser productionServer /va  
```  
  
 ファイル システムに保存されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを実行するには、次のコードを使用します。  
  
```  
dtexec /f "c:\pkgOne.dtsx"   
```  
  
 ファイル システムに保存されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行、およびログ オプションの指定を行うには、次のコードを使用します。  
  
```  
dtexec /f "c:\pkgOne.dtsx" /l "DTS.LogProviderTextFile;c:\log.txt"  
```  
  
 Windows 認証が使用され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のローカル インスタンスに保存されているパッケージの実行、および実行前にバージョンの確認を行うには、次のコードを使用します。  
  
```  
dtexec /sq pkgOne /verifyv {c200e360-38c5-11c5-11ce-ae62-08002b2b79ef}  
```  
  
 ファイル システムに保存されているが、外部で構成されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを実行するには、次のコードを使用します。  
  
```  
dtexec /f "c:\pkgOne.dtsx" /conf "c:\pkgOneConfig.cfg"  
```  
  
> [!NOTE]  
>  /SQL、/DTS、または /FILE オプションの *package_path* または *filespec* 引数は、パスまたはファイル名に空白文字が含まれる場合、引用符で囲む必要があります。 引数を引用符で囲まないと、空白文字を引数に含めることはできません。  
  
 **ログ オプション**  
  
 ログ エントリの種類が A、B、C の 3 つある場合、次のように、パラメーターを指定せずに **ConsoleLog** オプションを使用すると、3 つすべてのログの種類がすべてのフィールドと共に表示されます。  
  
```  
/CONSOLELOG  
```  
  
 次のオプションを指定すると、すべてのログの種類が、Name 列および Message 列のみと共に表示されます。  
  
```  
/CONSOLELOG NM  
```  
  
 次のオプションを指定すると、A の種類のログ エントリのみが、すべての列と共に表示されます。  
  
```  
/CONSOLELOG I;LogEntryTypeA  
```  
  
 次のオプションを指定すると、A の種類のログ エントリのみが Name 列および Message 列と共に表示されます。  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA  
```  
  
 次のオプションを指定すると、A および B の種類のログ エントリが表示されます。  
  
```  
/CONSOLELOG I;LogEntryTypeA;LogEntryTypeB  
```  
  
 複数の **ConsoleLog** オプションを指定すると、同じ結果を得ることができます。  
  
```  
/CONSOLELOG I;LogEntryTypeA /CONSOLELOG I;LogEntryTypeB  
```  
  
 パラメーターなしで **ConsoleLog** オプションを指定すると、すべてのフィールドが表示されます。 次の指定に *list_options* パラメーターを含めると、A の種類のログ エントリのみがすべてのフィールドと共に表示されます。  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA /CONSOLELOG  
```  
  
 次の例では、種類 A のログ エントリを除くすべてのログ エントリ (種類 B と C) が表示されます。  
  
```  
/CONSOLELOG E;LogEntryTypeA  
```  
  
 次のように複数の **ConsoleLog** オプションを使用し、単一のログ エントリを除外することで、前の例と同じ結果が得られます。  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG E;LogEntryTypeA  
/CONSOLELOG E;LogEntryTypeA;LogEntryTypeA  
```  
  
 ログ ファイルの種類が包含一覧と除外一覧の両方に指定されている場合、そのログ ファイルは除外されるため、次の例ではログ メッセージは表示されません。  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG I;LogEntryTypeA  
```  
  
 **SET オプション**  
  
 **/SET** オプションの使用方法の例を次に示します。これは、パッケージのプロパティ値または変数値をコマンド ラインからパッケージを起動するときに変更します。  
  
```  
/SET \package\DataFlowTask.Variables[User::MyVariable].Value;newValue  
```  
  
 **プロジェクトのオプション**  
  
 次の例は、`/Project` オプションと `/Package` オプションを使用する方法を示しています。  
  
```  
/Project c:\project.ispac /Package Package1.dtsx  
```  
  
 次の例は、`/Project` オプションと `/Package` オプションを使用してパッケージとプロジェクトのパラメーターを設定する方法を示しています。  
  
```  
/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1  
  
```  
  
 **ISServer のオプション**  
  
 次の例は `/ISServer` オプションを使用する方法を示しています。  
  
```  
dtexec /isserver "\SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "."  
```  
  
 次の例は、`/ISServer` オプションを使用してプロジェクトと接続マネージャーのパラメーターを設定する方法を示しています。  
  
```  
/Server localhost /ISServer "\SSISDB\MyFolder\Integration Services Project1\Package.dtsx" /Par "$Project::ProjectParameter(Int32)";1 /Par "CM.SourceServer.InitialCatalog";SourceDB  
  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 [SQL Server Data Tools でのパッケージの実行](../run-a-package-in-sql-server-data-tools.md)  
  
## <a name="related-content"></a>関連コンテンツ  
 [www.mattmasson.com](www.mattmasson.com) のブログ エントリ「 [終了コード、DTEXEC、および SSIS カタログ](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/)」  
  
  
