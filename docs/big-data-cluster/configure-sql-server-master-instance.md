---
title: SQL Server マスター インスタンスの構成
titleSuffix: Configure SQL Server master instance of Big Data Cluster
description: SQL Server ビッグ データ クラスターのマスター インスタンスの構成
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3937152161cdfb1124c8761c61ac20cb7218b9d8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784336"
---
# <a name="configure-master-instance-of-big-data-clusters-2019"></a>[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] のマスター インスタンスの構成

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] のマスター インスタンスを構成します。

展開時に SQL Server マスター インスタンスのサーバー構成設定を構成することはできません。 この記事では、SQL Server のエディションなどの設定を構成する方法、SQL Server エージェントを有効または無効にする方法、特定のトレース フラグを有効にする方法、カスタマー フィードバックを有効/無効にする方法に関する一時的な回避策について説明します。

これらのいずれかの設定を変更するには、次の手順に従います。

1. ターゲット設定を含むカスタム `mssql-custom.conf` ファイルを作成します。 次の例では、SQL エージェント、テレメトリを有効にし、Enterprise Edition の PID を設定し、トレース フラグ 1204 を有効にします。

   ```
   [sqlagent]
   enabled=true
   
   [telemetry]
   customerfeedback=true
   userRequestedLocalAuditDirectory = /tmp/audit

   [DEFAULT]
   pid = Enterprise

   [traceflag]
   traceflag0 = 1204
   ```

1. `mssql-custom.conf` ファイルを `master-0` ポッドの `mssql-server` コンテナー内の `/var/opt/mssql` にコピーします。 `<namespaceName>` をビッグ データ クラスター名に置き換えます。

   ```bash
   kubectl cp mssql-custom.conf master-0:/var/opt/mssql/mssql-custom.conf -c mssql-server -n <namespaceName>
   ```

1. SQL Server インスタンスを再起動します。  `<namespaceName>` をビッグ データ クラスター名に置き換えます。

   ```bash
   kubectl exec -it master-0  -c mssql-server -n <namespaceName> -- /bin/bash
   supervisorctl restart mssql-server
   exit
   ```

> [!IMPORTANT]
> SQL Server マスター インスタンスが可用性グループ構成内にある場合は、すべての `master` ポッドに `mssql-custom.conf` ファイルをコピーします。 再起動のたびにフェールオーバーが発生するので、このアクティビティのタイミングをダウンタイム期間中にする必要があることに注意してください。

## <a name="known-limitations"></a>既知の制限事項

- 上記の手順では、Kubernetes クラスター管理者のアクセス許可が必要です
- 展開後に、ビッグ データ クラスターの SQL Server マスター インスタンスのサーバーの照合順序を変更することはできません。

## <a name="next-steps"></a>次のステップ

SQL Server ビッグ データ クラスターの展開の詳細については、「[SQL Server ビッグ データ クラスターの使用を開始する](deploy-get-started.md)」を参照してください。