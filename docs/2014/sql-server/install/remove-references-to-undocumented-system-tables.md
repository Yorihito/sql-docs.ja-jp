---
title: ドキュメントに記載されていないシステムテーブルへの参照を削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45c38038ee3d3214e4303c0ddbe0110be926c37e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059200"
---
# <a name="remove-references-to-undocumented-system-tables"></a>ドキュメントに記載されていないシステム テーブルへの参照の削除
  以前のリリースのドキュメントには記載されていなかった多くのシステム テーブルが変更されたか、存在しなくなりました。そのため、アップグレード後にそのようなシステム テーブルを使用すると、エラーが発生する場合があります。 アップグレード アドバイザーはシステム テーブル名への参照を検索するので、システム テーブルと同じ名前のユーザー テーブルへの参照を報告します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 ドキュメントに記載されていない以下のシステム テーブルは削除されました。  
  
-   **spt_datatype_info**  
  
-   **spt_datatype_info_ext**  
  
-   **spt_provider_types**  
  
-   **spt_server_info**  
  
-   **spt_values**  
  
-   **sysfulltextnotify**  
  
-   **syslocks**  
  
-   **sysproperties**  
  
-   **sysprotects_aux**  
  
-   **sysprotects_view**  
  
-   **SYSREMOTE_CATALOGS**  
  
-   **SYSREMOTE_COLUMN_PRIVILEGES**  
  
-   **SYSREMOTE_COLUMNS**  
  
-   **SYSREMOTE_FOREIGN_KEYS**  
  
-   **SYSREMOTE_INDEXES**  
  
-   **SYSREMOTE_PRIMARY_KEYS**  
  
-   **SYSREMOTE_PROVIDER_TYPES**  
  
-   **SYSREMOTE_SCHEMATA**  
  
-   **SYSREMOTE_STATISTICS**  
  
-   **SYSREMOTE_TABLE_PRIVILEGES**  
  
-   **SYSREMOTE_TABLES**  
  
-   **SYSREMOTE_VIEWS**  
  
-   **syssegments**  
  
-   **sysxlogins**  
  
## <a name="corrective-action"></a>修正措置  
 次の表に従ってアプリケーションを修正してください。  
  
|以前のシステム ストアド プロシージャ|用途|  
|----------------|---------|  
|**sysfulltextnotify**|OBJECTPROPERTYEX 関数の**TableFulltextPendingChanges**プロパティ。|  
|**syslocks**|**dm_tran_locks**動的管理ビュー、sp_lock、または**sys.syslockinfo**互換性ビュー。|  
|**sysproperties**|**extended_properties**カタログビューまたは**fn_listextendedproperty**関数|  
|**sysxlogins**|**server_principals**カタログビューまたは**syslogins**互換性ビュー。|  
|すべての**spt_** テーブル|置き換えることはできません|  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
