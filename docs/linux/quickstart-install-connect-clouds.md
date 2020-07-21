---
title: クラウドで SQL Server (on Linux) を開始する
titleSuffix: SQL Server
description: このクイック スタートでは、任意のクラウドで SQL Server on Linux を実行する方法を示します。
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: cb24499b411d288e1e79b49d202fba63b251a805
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897544"
---
# <a name="quickstart-run-sql-server-in-the-cloud"></a>クイック スタート:クラウドで SQL Server を実行する
[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

このクイックスタートでは、任意のクラウドで Red Hat Enterprise Linux (RHEL)、SUSE Linux Enterprise Server (SLES)、または Ubuntu に SQL Server をインストールします。 「[Azure portal での Linux SQL Server 仮想マシンのプロビジョニング](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)」に進み、Azure で SQL Server on Linux を実行します。

> [!NOTE]
> SQL Server の有料版を実行する場合、ライセンスを持ち込む必要があります (BYOL)。

## <a name="amazon-web-services"></a>アマゾン ウェブ サービス
1.  少なくとも 2 GB のメモリを備えた Linux AMI をマーケットプレースから作成します 
    * [RHEL 7.3+](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2+](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  ssh で AMI に接続します
1.  選択した Linux ディストリビューションのクイックスタートに従います。 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  リモート接続用に構成します。 
    * [Amazon EC2 コンソール]( https://console.aws.amazon.com/ec2/)を開きます
    * ナビゲーション ウィンドウで **[セキュリティ グループ]** を選択します。 
    * **[受信]、[編集]、[規則の追加]** の順に選択します
    * SQL Server がリッスンするポート (既定の TCP ポート 1433) でトラフィックを許可する受信規則を追加します

    
## <a name="digital-ocean"></a>Digital Ocean
1. [コントロール パネル](https://cloud.digitalocean.com/login)にログインし、[create a droplet]\(droplet の作成\) をクリックします
1. メモリが 2 GB 以上の Ubuntu 16.04 droplet を選択します
1. ssh で droplet に接続します
1. 「[Ubuntu クイックスタート](quickstart-install-connect-ubuntu.md)」に従います。
1. リモート接続用に構成します。
    * [コントロール パネル] の上部にある **[ネットワーク]** リンクをたどり、 **[ファイアウォール]** を選択します。
    * SQL Server がリッスンするポート (既定の TCP ポート 1433) でトラフィックを許可する受信規則を追加します
    
## <a name="google-cloud-platform"></a>Google Cloud Platform
1.  Cloud Launcher からメモリが 2 GB 以上の Linux イメージを作成します 
    * [RHEL 7.3+](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP4](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  ssh でイメージに接続します
1.  選択した Linux ディストリビューションのクイックスタートに従います。 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  リモート接続用に構成します。 
    * 「[ファイアウォール規則](https://console.cloud.google.com/networking/firewalls)」に進みます
    * SQL Server がリッスンするポート (既定の TCP ポート 1433) でトラフィックを許可する受信規則を追加します
