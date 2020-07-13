---
title: SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 463c570e-9f75-4653-b3b8-4d61753b0013
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6363dd09dba21273e57b6b087002000bec4e54dc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012600"
---
# <a name="file-locations-for-default-and-named-instances-of-sql-server"></a>SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールは、1 つ以上の別個のインスタンスで構成されます。 既定のインスタンスか名前付きインスタンスかにかかわらず、各インスタンスには、それぞれ専用のプログラム ファイルとデータ ファイルが用意されます。さらに、コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインスタンスが使用する共有ファイル セットもあります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]が含まれている場合は、これらの各コンポーネントで使用するデータと実行ファイルのセット、およびすべてのコンポーネントが使用する共有ファイルが用意されます。  
  
 コンポーネントごとにインストール場所を分けるため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス内の各コンポーネントについて一意のインスタンス ID が生成されます。  
  
> [!IMPORTANT]  
>  リムーバブル ディスク ドライブ、圧縮を使用するファイル システム、システム ファイルが存在するディレクトリ、およびフェールオーバー クラスター インスタンス上の共有ドライブには、プログラム ファイルとデータ ファイルをインストールすることができません。  
>   
>  システム データベース (master、model、MSDB、および tempdb) と [!INCLUDE[ssDE](../../includes/ssde-md.md)] のユーザー データベースは、ストレージ オプションとしてサーバー メッセージ ブロック (SMB) ファイル サーバーを指定してインストールできます。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スタンドアロン インストールと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インストール (FCI) の両方に当てはまります。 詳細については、「 [SQL Server をストレージ オプションとして SMB ファイル共有にインストールする](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md)」を参照してください。  
>   
>  Binn、Data、Ftdata、HTML、1033 の各ディレクトリとその内容は削除しないでください。 他のディレクトリは必要に応じて削除できますが、削除した機能やデータを元に戻すには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をいったんアンインストールしてからインストールし直す必要があります。 HTML ディレクトリ内のすべての .htm ファイルは、削除も修正もしないでください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のツールを正常に機能させるには、これらのファイルが必要です。  
  
## <a name="shared-files-for-all-instances-of-ssnoversion"></a>のすべてのインスタンスで共有されるファイル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 1台のコンピューター上のすべてのインスタンスで使用される共通ファイルは、フォルダーにインストールされ [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)] ます。ここで、 \<*drive*> は、コンポーネントがインストールされているドライブ文字です。 既定値は、通常はドライブ C です。  
  
## <a name="file-locations-and-registry-mapping"></a>ファイルの場所とレジストリのマッピング  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの実行時には、サーバー コンポーネントごとにインスタンス ID が生成されます。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リリースのサーバー コンポーネントは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。  
  
 既定のインスタンス ID は、次の形式を使用して作成されます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]を表す "MSSQL" に、メジャー バージョン番号、アンダースコアおよびマイナー番号 (該当する場合)、ピリオド、およびインスタンス名を連結した形式  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を表す "MSAS" に、メジャー バージョン番号、アンダースコアおよびマイナー番号 (該当する場合)、ピリオド、およびインスタンス名を連結した形式  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を表す "MSRS" に、メジャー バージョン番号、アンダースコアおよびマイナー番号 (該当する場合)、ピリオド、およびインスタンス名を連結した形式  
  
 このリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における既定のインスタンス ID の例を次に示します。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の既定のインスタンスの場合: MSSQL12.MSSQLSERVER。  
  
-   [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] の既定のインスタンスの場合: MSAS12.MSSQLSERVER。  
  
-   "MyInstance" という名前の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスの場合: MSSQL12.MyInstance。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssDE](../../includes/ssde-md.md)] を含み、名前が "MyInstance" で、インストール先が既定のディレクトリである [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の名前付きインスタンスの場合、ディレクトリ構造は次のようになります。  
  
-   C:\Program Files\Microsoft SQL Server\MSSQL12.MyInstance\  
  
-   C:\Program Files\Microsoft SQL Server\MSAS12.MyInstance\  
  
 インスタンス ID には任意の値を指定できますが、特殊文字や予約されたキーワードは使用しないでください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ時に、既定以外のインスタンス ID を指定できます。 ではなく、 \<Program Files> \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<custom path> \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 既定のインストールディレクトリを変更することをユーザーが選択した場合は、が使用されます。 アンダースコア (_) で始まるインスタンス ID、またはシャープ記号 (#) かドル記号 ($) を含むインスタンス ID はサポートされていないことに注意してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] とクライアント コンポーネントはインスタンス対応でないため、インスタンス ID は割り当てられません。 既定では、インスタンス対応でないコンポーネントが単一のディレクトリ [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]にインストールされます。 1 つの共有コンポーネントのインストール パスを変更すると、他の共有コンポーネントのパスも変更されます。 後続のインストールでは、最初のインストールと同じディレクトリに、インスタンス対応でないコンポーネントがインストールされます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール後にインスタンスの名前を変更することをサポートする唯一のコンポーネントです。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの名前を変更しても、インスタンス ID は変更されません。 インスタンスの名前変更が完了した後も、ディレクトリとレジストリ キーは、インストール時に作成されたインスタンス ID を引き続き使用します。  
  
 インスタンス対応のコンポーネントの場合は、HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*Instance_ID*> の下にレジストリ ハイブが作成されます。 たとえば、次のように入力します。  
  
-   、Hklm\software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12.MyInstance  
  
-   、Hklm\software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ msas12。MyInstance  
  
-   、Hklm\software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、msrs12。MyInstance  
  
 このレジストリは、インスタンス ID とインスタンス名のマッピングも管理します。 インスタンス ID とインスタンス名のマッピングは次のようになります。  
  
-   [HKEY_LOCAL_MACHINE \ ソフトウェア \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ インスタンス Nam/SQL] "InstanceName" = "MSSQL12.MSSQLSERVER"  
  
-   [HKEY_LOCAL_MACHINE \ ソフトウェア \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ インスタンス Nam/OLAP] "InstanceName" = "MSAS12.<INSTANCEID>"  
  
-   [HKEY_LOCAL_MACHINE \ ソフトウェア \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ インスタンス Nam/RS] "InstanceName" = "MSRS12"  
  
## <a name="specifying-file-paths"></a>ファイル パスの指定  
 セットアップ中、次の機能のインストール パスを変更できます。  
  
 セットアップでインストール パスが表示されるのは、ユーザーがインストール先フォルダーを構成できる機能のみです。  
  
|コンポーネント|既定<sup>のパス1、2</sup>|構成可能な<sup>3</sup>または固定パス|  
|---------------|---------------------------------|--------------------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] サーバー コンポーネント|\\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceID> \MSSQL12. \|事前|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] データ ファイル|\\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceID> \MSSQL12. \|事前|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー (server)|ファイル名 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ msas12。 \<InstanceID> \|事前|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ファイル|ファイル名 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ msas12。 \<InstanceID> \|事前|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー (report server)|ファイル名 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ msrs12。 \<InstanceID>\ Reporting Services\ReportServer\Bin \| 構成可能|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート マネージャー|ファイル名 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ msrs12。 \<InstanceID>\ レポート Services\ReportManager \| 固定パス|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|\<Install Directory>\ 120 \ DTS \| 構成可能<sup>4</sup>|  
|クライアント コンポーネント (bcp.exe および sqlcmd.exe を除く)|\<Install Directory>\ 120 \ ツール \| 構成可能<sup>4</sup>|  
|クライアント コンポーネント (bcp.exe および sqlcmd.exe)|\<Install Directory>\ クライアント SDK\ODBC\110\Tools\Binn|固定パス|  
|レプリケーションおよびサーバー側 COM オブジェクト|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM \\ <sup>5</sup>|固定パス|  
|データ変換ランタイム エンジン、データ変換パイプライン エンジン、および `dtexec` コマンド プロンプト ユーティリティ用の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネント DLL|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|固定パス|  
|DLL。次のマネージド接続をサポート: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Connections|固定パス|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がサポートする列挙子の型ごとの DLL|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\ForEachEnumerators|固定パス|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service、WMI プロバイダー|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]共有 \| 固定パス|  
|次のすべてのインスタンス間で共有されるコンポーネント: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]共有 \| 固定パス|  
  
 <sup>1</sup>ファイル \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \ フォルダーが制限されたアクセス許可で保護されていることを確認します。  
  
 <sup>2</sup>これらの場所の既定のドライブは*systemdrive*、通常はドライブ C です。  
  
 <sup>3</sup>子機能のインストールパスは、親機能のインストールパスによって決まります。  
  
 <sup>4</sup>1つのインストールパスは、とクライアントコンポーネントの間で共有され [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。 1 つのコンポーネントのインストール パスを変更すると、他のコンポーネントのパスも変更されます。 後続のインストールでは、最初のインストールと同じ場所にコンポーネントがインストールされます。  
  
 <sup>5</sup>このディレクトリは、コンピューター上ののすべてのインスタンスによって使用され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 コンピューター上のいずれかのインスタンスに更新を適用すると、このフォルダー内のファイルに対する変更内容が、コンピューター上のすべてのインスタンスに反映されます。 既存のインストールに機能を追加する場合、前にインストールした機能の場所は変更できません。また、新しい機能のインストール場所を指定することもできません。 セットアップで以前に設定したディレクトリに追加機能をインストールするか、製品をいったんアンインストールしてインストールし直す必要があります。  
  
> [!NOTE]  
>  クラスター化された構成では、クラスターのすべてのノードで使用できるローカル ドライブを選択する必要があります。  
  
 セットアップ時にサーバー コンポーネントまたはデータ ファイルのインストール パスを指定する場合、プログラム ファイルとデータ ファイルについては、指定した場所に加えてインスタンス ID も使用されます。 ツールおよびその他の共有ファイルについては、インスタンス ID は使用されません。 また、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プログラム ファイルとデータ ファイルについてもインスタンス ID は使用されませんが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] リポジトリについてはインスタンス ID が使用されます。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 機能のインストール パスを設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップではそのパスがルート ディレクトリとして使用されます。このルート ディレクトリは、SQL データ ファイルを含め、そのインストールで使用するすべてのインスタンス固有フォルダーに適用されます。 この場合、ルートを "C:\Program files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. \<InstanceName> " に設定すると、\ MSSQL \\ "は、インスタンス固有のディレクトリをそのパスの末尾に追加します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザード (セットアップ UI モード) で USESYSDB アップグレード機能の使用を選択すると、製品が再帰的フォルダー階層にインストールされることがよくあります。 たとえば、 \<*SQLProgramFiles*> \mssql12\mssql\ MSSQL10_50 \mssql\data のように \\ なります。 USESYSDB 機能を使用する場合は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 機能ではなく、SQL データ ファイル機能のインストール パスを設定してください。  
  
> [!NOTE]
>  データ ファイルは、常に、Data という名前の子ディレクトリに格納されているものと見なされます。 たとえば、C:\Program files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. \<InstanceName> を指定します。\ は、アップグレード時にシステムデータベースのデータディレクトリへのルートパスを指定します。このとき、データファイルは C:\Program files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. \<InstanceName> にあります。\Mssql\data  
  
## <a name="see-also"></a>参照  
 [データベースエンジンの構成-データディレクトリ](../../../2014/sql-server/install/database-engine-configuration-data-directories.md)   
 [Analysis Services の構成 - データ ディレクトリ](../../../2014/sql-server/install/analysis-services-configuration-data-directories.md)  
  
  
