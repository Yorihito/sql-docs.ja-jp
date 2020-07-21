---
title: curl を使用して HDFS にデータを読み込む |Microsoft Docs
titleSuffix: SQL Server big data clusters
description: curl を使用して、SQL Server 2019 ビッグ データ クラスター上の HDFS にデータを読み込みます。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 45974b3b59a97af8e432f059c0facfb27ece2fbd
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606854"
---
# <a name="use-curl-to-load-data-into-hdfs-on-big-data-clusters-2019"></a>curl を使用して [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] 上の HDFS にデータを読み込む

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、**curl** を使用して [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] 上の HDFS にデータを読み込む方法について説明します。

## <a name="prerequisites"></a><a id="prereqs"></a> 前提条件

- [ビッグ データ クラスターにサンプル データを読み込む](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>サービスの外部 IP を取得する

WebHDFS は展開が完了すると開始され、そのアクセスは Knox を経由します。 Knox エンドポイントは、**gateway-svc-external** という Kubernetes サービスを介して公開されます。  ファイルをアップロードまたはダウンロードするために必要な WebHDFS URL を作成するには、**gateway-svc-external** サービスの外部 IP アドレスとビッグ データ クラスターの名前が必要です。 次のコマンドを実行して、**gateway-svc-external** サービスの外部 IP アドレスを取得できます。

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` は、ここでは、展開構成ファイル内に指定したクラスターの名前です。 既定の名前は `mssql-cluster` です。

## <a name="construct-the-url-to-access-webhdfs"></a>WebHDFS にアクセスするための URL を作成する

次のように、WebHDFS にアクセスするための URL を作成できます。

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

次に例を示します。

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>ファイルの一覧表示

**hdfs:///product_review_data** の下のファイルを一覧表示するには、次の curl コマンドを使用します。

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>ローカル ファイルを HDFS に配置する

**test.csv** という新しいファイルをローカル ディレクトリから product_review_data ディレクトリに配置するには、次の curl コマンドを使用します (**Content-Type** パラメーターは必須です)。

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>ディレクトリを作成する

`hdfs:///` の下に **test** というディレクトリを作成するには、次のコマンドを使用します。

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>次のステップ

SQL Server ビッグ データ クラスターの詳細については、「[SQL Server ビッグ データ クラスターとは](big-data-cluster-overview.md)」を参照してください。
