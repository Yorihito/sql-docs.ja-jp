---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 197d485fe851298a8e8d365c9fd1a52bf1251101
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553458"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21871|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21871|  
|メッセージ テキスト|データベース %s のパブリッシャー %s がリダイレクトされていません。|  
  
## <a name="explanation"></a>説明  
 `sp_validate_replica_hosts_as_publishers` は、ディストリビューション データベースのテーブル MSredirected_publishers で、識別されたパブリッシャーおよびパブリッシャー データベースのエントリがあるかどうかをチェックします。  エントリが見つからない場合、`sp_validate_replica_hosts_as_publishers` はエラー 21871 を返します。  
  
## <a name="user-action"></a>ユーザーの操作  
 `sp_validate_replica_hosts_as_publishers` は、リダイレクトされたパブリッシャーにのみ関連しています。 パブリッシャー データベースが可用性グループのメンバーである場合、ストアド プロシージャ `sp_redirect_publisher` を使用して、パブリッシャーおよびパブリッシャー データベースを可用性グループの可用性グループ リスナー名に関連付けます。  
  
  
