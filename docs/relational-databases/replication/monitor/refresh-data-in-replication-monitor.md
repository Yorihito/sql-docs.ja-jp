---
title: レプリケーション モニターのデータの更新 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: be4dde11a67c0391f753c29b411baf9ccb25d804
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770521"
---
# <a name="refresh-data-in-replication-monitor"></a>レプリケーション モニターのデータの更新
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  レプリケーション モニターでは、メイン ウィンドウと詳細ウィンドウ (メイン ウィンドウから起動するウィンドウ) を自動または手動で最新の情報に更新できます。 ウィンドウを手動で最新の情報に更新する場合は、F5 キーを押します。 既定では、メイン ウィンドウは 5 秒ごとに自動で最新の情報に更新されます。この更新頻度は、パブリッシャーごとにカスタマイズできます。  
  
 レプリケーション モニターに表示されるデータはキャッシュからクエリされます。キャッシュとレプリケーション モニターの更新の関係に関する詳細については、「[キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)」を参照してください。 レプリケーション モニターの起動の詳細については、「[レプリケーション モニターの開始](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)」を参照してください。  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a>レプリケーション モニターの更新オプションを設定するには
  
1.  パブリケーション モニターの左ペインでパブリッシャーを右クリックしてから、 **[パブリッシャーの設定]** をクリックします。  
  
2.  **[パブリッシャーの設定]** ダイアログ ボックスで、 **[自動更新]** または **[更新頻度]** オプションを設定します。 **[自動更新]** 設定は、レプリケーション モニターのメイン ウィンドウに影響します。 **[更新頻度]** 設定は、自動更新に設定されているすべての詳細ウィンドウにも影響します (この設定の変更に影響を受けるのは、変更後に開かれた詳細ウィンドウのみです)。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a>詳細ウィンドウを自動更新するように指定するには  
  
1.  レプリケーション モニターで詳細ウィンドウを開きます。 例:  
  
    1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
    2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
    3.  サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。  
  
2.  **[サブスクリプション \<SubscriptionName>]** 詳細ウィンドウで、 **[アクション]** をクリックし、 **[自動更新]** をクリックします。 更新頻度は、 **[パブリッシャーの設定]** ダイアログ ボックスの **[更新頻度]** 設定によって決まります。  
  
## <a name="see-also"></a>参照  
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
