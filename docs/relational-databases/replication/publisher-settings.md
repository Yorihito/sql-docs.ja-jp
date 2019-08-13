---
title: SQL Server レプリケーションの [パブリッシャーの設定] ダイアログ ボックス | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 79685cf22fc0adda979611c23111ab28074de386
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2019
ms.locfileid: "68763956"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a>SQL Server レプリケーションの [パブリッシャーの設定] ダイアログ ボックス
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  **[パブリッシャーの設定]** ダイアログ ボックスを使用すると、レプリケーション モニターの左ペインに追加されているパブリッシャーの設定を変更できます。  
  
## <a name="options"></a>オプション  
 **[パブリッシャー接続]**  
 クリックすると、 **[サーバーへの接続]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは、レプリケーション モニターがパブリッシャーに接続するときに使用する接続プロパティおよび資格情報を表示および変更できます。  
  
 **[ディストリビューター接続]**  
 パブリッシャーがリモート ディストリビューターを使用する場合にのみ表示されます。 クリックすると、 **[サーバーへの接続]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは、レプリケーション モニターがリモート ディストリビューターに接続するときに使用する接続プロパティおよび資格情報を表示および変更できます。  
  
 **[レプリケーション モニターが起動したときに自動的に接続する]**  
 オンにした場合、レプリケーション モニターは自動的にディストリビューターに接続し、ダイアログ ボックスの上部のグリッドで選択されているパブリッシャーの状態情報を取得します。 このチェック ボックスがオフの場合は、レプリケーション モニターを起動した後に手動でパブリッシャーに接続する必要があります。つまり、レプリケーション モニターの左ペインでパブリッシャーを右クリックし、 **[接続]** をクリックします。  
  
 **[このパブリッシャーとパブリケーションのステータスを自動的に更新する]**  
 オンにした場合、レプリケーション モニターは、ダイアログ ボックスの上部のグリッドで選択されているパブリッシャーの状態情報を自動的に更新します。 このオプションがオンの場合、レプリケーション モニターは、パブリッシャーとそのパブリケーションの状態情報についてディストリビューターをポーリングします。 ポーリング間隔は、 **[更新頻度]** オプションで設定します。 レプリケーション モニターでの更新の詳細については、「[キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)」を参照してください。  
  
 **[更新頻度]**  
 レプリケーション モニターが状態についてディストリビューターをポーリングする間隔 (秒数) を入力します。 小さい値を指定すると、ポーリングがより短い間隔で行われ、その結果、監視対象のパブリッシャーが数多くある場合にディストリビューター側のパフォーマンスが影響を受ける可能性があります。 システムをテストしながら適切な値を見つけてください。 **[更新頻度]** 設定は、レプリケーション モニターのいずれかの詳細ウィンドウで **[自動更新]** を選択している場合にも使用されます。  
  
 **[このパブリッシャーを次のグループに表示する]**  
 一覧からパブリッシャー グループを選択します。 パブリッシャーは、左ペインでこのグループの下に表示されます。 グループはパブリッシャーを整理するもので、レプリケーションの動作には影響を与えません。  
  
 **[新しいグループ]**  
 クリックすると、新しいパブリッシャー グループを作成できます。 パブリッシャー グループを利用すると、レプリケーション モニター内でパブリッシャーを容易に整理できます。 グループは、データのレプリケーションや、レプリケーション トポロジ内のサーバー間のリレーションシップには影響を与えません。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
