---
title: 履歴の保有期間の設定 (SSMS)
description: SQL Server Management Studio (SSMS) でディストリビューション データベースの履歴の保有期間を設定する方法について説明します。
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: bc04a0b78c93666b4213acea3a1f59af5dc5b5fb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767652"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>履歴の保有期間の設定 (SQL Server Management Studio)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  **[ディストリビューション データベースのプロパティ - \<DistributionDatabase>]** ダイアログ ボックスの **[全般]** ページで、履歴の保持期間を指定します。 この設定は、レプリケーション エージェントの履歴を保持する期間を制御します。 このページは、 **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページから使用できます。 このダイアログ ボックスへのアクセスの詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
### <a name="to-specify-the-history-retention-period"></a>履歴の保有期間を指定するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページで、ディストリビューション データベースのプロパティ ボタン ( **...** ) をクリックします。  
  
2.  **[レプリケーション パフォーマンス履歴を保存する最小期間]** ボックスに値を入力します。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)  
  
  
