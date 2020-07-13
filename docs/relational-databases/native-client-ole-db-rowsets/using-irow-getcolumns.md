---
title: IRow::GetColumns の使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 092c573e808aefc0f35f04e73b54e150a62bebac
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86013077"
---
# <a name="using-irowgetcolumns"></a>IRow::GetColumns の使用
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **IRow** の実装では、列に対して順方向専用の順次アクセスを実行できます。 **IRow::GetColumns** を 1 回だけ呼び出して、行内のすべての列にアクセスすることができます。また、行内の複数の列にアクセスするたびに、毎回 **IRow::GetColumns** を呼び出すこともできます。  
  
 **IRow::GetColumns** を複数回呼び出す場合は、呼び出しが重ならないようにする必要があります。 たとえば、1 回目に **IRow::GetColumns** を呼び出すときに列 1、2、3 を取得する場合、2 回目に **IRow::GetColumns** を呼び出すときには列 4、5、6 を取得する必要があります。 **IRow::GetColumns** の呼び出しが重なると、状態フラグ (DBCOLUMNACCESS の dwstatus フィールド) が DBSTATUS_E_UNAVAILABLE に設定されます。  
  
## <a name="see-also"></a>参照  
 [IRow による 1 行のフェッチ](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
