---
title: '[ジョブのスケジュール選択]'
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.pickscheduleforjob.f1
helpviewer_keywords:
- Pick Schedule for Job dialog box
ms.assetid: 6de2025d-c25c-47b9-9a25-18c294935c15
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8b7da81bd6c0a54c96367fc24cc742fce6700974
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75247617"
---
# <a name="pick-schedule-for-job"></a>[ジョブのスケジュール選択]
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このダイアログを使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの既存のスケジュールを選択します。  
  
## <a name="options"></a>オプション  
**[利用可能なスケジュール]**  
このジョブで利用可能なスケジュールの一覧を表示します。 ジョブとスケジュールの所有者は同じである必要があるので、この一覧には、このジョブの所有者が所有しているスケジュールだけが表示されます。  
  
**Name**  
スケジュールの名前を表示します。  
  
**有効**  
スケジュールが有効な場合に選択されます。  
  
**説明**  
ジョブを実行するスケジュールの条件を説明します。  
  
**[スケジュール済みのジョブ]**  
スケジュールにアタッチされているジョブの番号を表示します。 番号をクリックすると、ジョブのプロパティが表示されます。  
  
**Properties**  
**[ジョブ スケジュールのプロパティ]** ダイアログを表示します。このダイアログには、スケジュールに関する情報が表示されます。  
  
## <a name="see-also"></a>参照  
[スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
