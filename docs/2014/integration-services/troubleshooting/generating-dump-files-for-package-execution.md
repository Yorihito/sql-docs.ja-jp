---
title: パッケージ実行用のダンプ ファイルを生成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 61ef1731-cb3a-4afb-b4a4-059b04aeade0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61e511aaff6c3c77338211537a685f8a1dc82981
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420609"
---
# <a name="generating-dump-files-for-package-execution"></a>パッケージ実行用のダンプ ファイルを生成する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、パッケージの実行に関する情報を提供するデバッグ ダンプ ファイルを作成できます。 このファイル内の情報は、パッケージの実行に関する問題のトラブルシューティングに役立ちます。  
  
> [!NOTE]  
>  デバッグ ダンプ ファイルには機密情報が含まれている場合があります。 機密情報を保護するには、アクセス制御リスト (ACL) を使用してこのファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーすることができます。 たとえば、デバッグ ファイルを [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにプロジェクトを配置すると、そのプロジェクトに含まれているパッケージの実行に関する情報を提供するダンプ ファイルを作成できます。 ISServerExec.exe プロセスが終了すると、ダンプ ファイルが作成されます。 **[パッケージの実行]** ダイアログ ボックスの **[エラー時にダンプする]** オプションを選択することにより、パッケージの実行中にエラーが発生したらダンプ ファイルが作成されるように指定できます。 また、次のストアド プロシージャを使用することもできます。  
  
-   [catalog.set_execution_parameter_value &#40;SSISDB データベース&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
     パッケージの実行中にエラーまたはイベントが発生したとき、および特定のイベントが発生したときにダンプ ファイルが作成されるように構成する場合に、このストアド プロシージャを呼び出します。  
  
-   [catalog.create_execution_dump](/sql/integration-services/system-stored-procedures/catalog-create-execution-dump)  
  
     実行中のパッケージを一時停止してダンプ ファイルを作成する場合に、このストアド プロシージャを呼び出します。  
  
 パッケージ配置モデルを使用してパッケージを配置する場合は、**dtexec** ユーティリティまたは **dtutil** ユーティリティを使用して、コマンド ラインでデバッグ ダンプ オプションを指定することによって、デバッグ ダンプ ファイルを作成します。 詳細については、「 [dtexec ユーティリティ](../packages/dtexec-utility.md) 」と「 [dtutil ユーティリティ](../dtutil-utility.md)」を参照してください。 パッケージ配置モデルの詳細については、「[プロジェクトとパッケージの配置](../packages/deploy-integration-services-ssis-projects-and-packages.md)」および「 [SSIS&#41;&#40;パッケージ配置](../packages/legacy-package-deployment-ssis.md)」を参照してください。  
  
## <a name="debug-dump-file-format"></a>デバッグ ダンプ ファイルの形式  
 デバッグ ダンプ オプションを指定した場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって作成されるデバッグ ダンプ ファイルを次に示します。  
  
-   .mdmp デバッグ ダンプ ファイル。 これはバイナリ ファイルです。  
  
-   .tmp デバッグ ダンプ ファイル。 これはテキスト形式のファイルです。  
  
 既定では、は、次の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ファイルをフォルダーに保管し* \<drive> ます。*  
  
 次の表では、.tmp ファイル内の特定のセクションのみについて説明します。 .tmp ファイルには、次の表に記載されていないデータが他にも含まれています。  
  
|情報の種類|説明|例|  
|-------------------------|-----------------|-------------|  
|環境|オペレーティング システムのバージョン、メモリの使用量のデータ、プロセス ID、およびプロセス イメージ名。 環境情報は .tmp ファイルの先頭にあります。|# SSIS Textual Dump taken at 9/13/2007 1:50:34 PM<br /><br /> #PID 4120<br /><br /> #Image Name [C:\Program Files\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]<br /><br /> # OS major=6 minor=0 build=6000<br /><br /> # Running on 2 amd64 processors under WOW64<br /><br /> # Memory: 58% in use. Physical: 845M/2044M  Paging: 2404M/4095M (avail/total)|  
|ダイナミック リンク ライブラリ (DLL) のパスとバージョン|パッケージの処理中にシステムによって読み込まれる各 DLL のパスとバージョン番号。|# Loaded Module: c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)<br /><br /> # Loaded Module: C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)<br /><br /> # Loaded Module: C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)|  
|最新のメッセージ|システムで発行された最新のメッセージ。 各メッセージの時刻、種類、説明、およびスレッド ID が含まれます。|[M:1]   Ring buffer entry:              (*pRecord)<br /><br /> [1-2]       <<\<CRingBufferLogging::RingBufferLoggingRecord>>>  ( \@ 0282f1a8)<br /><br /> [E:3]         Time Stamp: 2007-09-13 13:50:32.786      (szTimeStamp)<br /><br /> [E:3]         Thread ID: 2368           (ThreadID)<br /><br /> [E:3]         Event Name: OnError                        (EventName)<br /><br /> [E:3]         Source Name:                (SourceName)<br /><br /> [E:3]         Source ID:                        (SourceID)<br /><br /> [E:3]         Execution ID:                 (ExecutionGUID)<br /><br /> [E:3]         Data Code: -1073446879              (DataCode)<br /><br /> [E:3]         説明: コンポーネントが見つからないか、登録されていないか、アップグレードできないか、コンポーネントに必要なインターフェイスが見つかりません。 このコンポーネントの連絡先情報は "" です。|  
  
## <a name="related-content"></a>関連コンテンツ  
 [Execute Package Dialog Box](../execute-package-dialog-box.md)  
  
  
