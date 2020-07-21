---
title: replay オプション (分散再生管理ツール) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3114d7c2a2a7908e4e010fbf5d80c7d332d264c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011622"
---
# <a name="replay-option-distributed-replay-administration-tool"></a>replay オプション (Distributed Replay 管理ツール)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散再生管理ツールは、 `DReplay.exe` 分散再生コントローラーとの通信に使用できるコマンドラインツールです。 このトピックでは、 **replay** コマンド ライン オプションとそれに対応する構文について説明します。

 **replay** オプションはイベント再生段階を開始します。ここでは、コントローラーは、指定されたクライアントに再生データをディスパッチし、分散再生を開始して、クライアントを同期します。 必要に応じて、再生に参加している各クライアントは再生アクティビティを記録し、結果トレース ファイルをローカルに保存できます。

 ![トピック リンク アイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン") 管理ツールの構文で使用される構文表記規則の詳細については、「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。

## <a name="syntax"></a>構文

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a>パラメーター
 **-m** *コントローラー*コントローラーのコンピューター名を指定します。 "`localhost`" または "`.`" を使用してローカル コンピューターを参照できます。

 **-m** パラメーターが指定されていない場合、ローカル コンピューターが使用されます。

 **-d** *controller_working_dir*中間ファイルを格納するコントローラー上のディレクトリを指定します。 **-d** パラメーターは必須です。

 これには次の要件があります。

-   ディレクトリはコントローラー上に置く必要があります。

-   ドライブ文字で始まる完全なパスを指定する必要があります (たとえば、 `c:\WorkingDir`)。

-   パスはバックスラッシュ "`\`" で終了することはできません。

-   UNC パスはサポートされません。

 **-o**クライアントの再生アクティビティをキャプチャし、クライアント構成ファイルの要素によって指定されたパスの結果トレースファイルに保存し `<ResultDirectory>` `DReplayClient.xml` ます。

 **-o** パラメーターが指定されていない場合は、結果トレース ファイルは生成されません。 コンソール出力は再生の最後に概要情報を返しますが、他の再生統計情報は提供されません。

 **-s** *target_server* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散ワークロードの再生に使用するの対象インスタンスを指定します。 このパラメーターは、 **server_name[\instance name]** の形式で指定します。

 "`localhost`" または "`.`" をターゲット サーバーとして使用することはできません。

 再生構成ファイル **の** セクションに `<Server>` 要素が指定されている場合、 `<ReplayOptions>` -s `DReplay.exe.replay.config`パラメーターは必要ありません。

 **-s** パラメーターが使用されている場合、再生構成ファイルの `<Server>` セクションの `<ReplayOptions>` 要素は無視されます。

 **-w** *クライアント*この必須パラメーターは、分散再生に参加するクライアントのコンピューター名を指定するコンマ区切りのリスト (スペースなし) です。 IP アドレスは指定できません。 コントローラーにクライアントが既に登録されている必要があることに注意してください。

> [!NOTE]
>  クライアント サービスが開始するときに、クライアント構成ファイルで指定されているコントローラーにクライアントが登録されます。

 **-c** *config_file*は、再生構成ファイルの完全なパスです。別の場所に格納されている場所を指定するために使用します。

 再生構成ファイル **の既定値を使用する場合、** -c `DReplay.exe.replay.config`パラメーターは必要ありません。

 **-f** *status_interval*状態を表示する頻度 (秒単位) を指定します。

 **-f** を指定しない場合は、既定の間隔は 30 秒です。

## <a name="examples"></a>例
 この例の分散再生では、変更された再生構成ファイル `DReplay.exe.replay.config`から多くの動作が派生しています。

-   **-m** パラメーターは、 `controller1` というコンピューターがコントローラーとして動作するように指定しています。 コントローラー サービスが別のコンピューターで実行されている場合は、コンピューター名を指定する必要があります。

-   **-d** パラメーターは、コントローラーの中間ファイルの場所として `c:\WorkingDir`を指定しています。

-   **-o** パラメーターは、指定された各クライアントが再生アクティビティをキャプチャし、それを結果トレース ファイルに保存するように指定しています。 注:構成ファイル内の `<ResultTrace>` 要素は、行数と結果セットが記録される場合に使用できます。

-   **-w** パラメーターは、 `client1` から `client4` までのコンピューターがクライアントとして分散再生に参加するように指定しています。

-   **-c** パラメーターは、変更された構成ファイル `DReplay.exe.replay.config`を指すために使用されています。

-   再生構成ファイル **の** 要素で `<Server>` 要素が指定されているため、 `<ReplayOptions>` -s `DReplay.exe.replay.config`パラメーターは必要ありません。

 管理ツールがコントローラーとは別のコンピューターから実行される場合、イベント再生段階は、次の構文で開始されます。

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 同期シーケンス モードを指定するために、 `<SequencingMode>` ファイルの `DReplay.exe.replay.config` 要素が値 `synchronization`と同じに設定されます。 再生構成ファイルの `<ResultTrace>` セクションは、行数を記録するように変更されます。 これらの変更を示したものが、次の XML 例です。

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 ストレス シーケンス モードを指定するために、 `<SequencingMode>` ファイルの `DReplay.exe.replay.config` 要素が値 `stress`と同じに設定されます。 `<ConnectTimeScale>` および `<ThinkTimeScale>` 要素が値 `50` に設定されます (50% を指定する場合)。 接続時間と待ち時間の詳細については、「 [Configure Distributed Replay](configure-distributed-replay.md)」を参照してください。 これらの変更を示したものが、次の XML 例です。

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a>アクセス許可
 対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。 ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。

 詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。

## <a name="see-also"></a>参照
 [トレースデータ](replay-trace-data.md)[の再生再生結果を確認](review-the-replay-results.md)[する:](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2)分散再生を使用して分散再生[SQL Server 分散再生フォーラム](https://social.technet.microsoft.com/Forums/sl/sqldru/)の分散再生[構成](configure-distributed-replay.md)し、SQL Server を使用して分散再生のロードテストを実行し、SQL Server を使用してをロードテストします。[第1部](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1) [SQL Server](sql-server-distributed-replay.md)


