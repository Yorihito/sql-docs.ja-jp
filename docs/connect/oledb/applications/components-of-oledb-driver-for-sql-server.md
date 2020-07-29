---
title: OLE DB Driver for SQL Server のコンポーネント | Microsoft Docs
description: OLE DB Driver for SQL Server のコンポーネント
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c88ef12d636dd5b10e1b7b3cd9418df3e058325b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007052"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のコンポーネント
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server には、次のコンポーネントが含まれています。  

|コンポーネント|説明|  
|---------------|-----------------|  
|msoledbsql.dll|OLE DB Driver for SQL Server のすべての機能を含む DLL (ダイナミック リンク ライブラリ) ファイル。|  
|msoledbsqlr.rll|OLE DB Driver for SQL Server ライブラリに付随するリソース ファイル。|   
|msoledbsql.h|OLE DB Driver for SQL Server を使用するために必要な新しい定義がすべて含まれている OLE DB Driver for SQL Server のヘッダー ファイル。 このヘッダー ファイルは、sqloledb.h ヘッダー ファイルに置き換わるものです。<br /><br /> 注:msoledbsql.h と sqloledb.h は、最初に sqloledb.h が定義されていれば、同じプログラムで参照できます。|  
|msoledbsql.lib|OLE DB Driver for SQL Server の一部である [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) 関数を直接呼び出すために必要なライブラリ ファイル。<br /><br /> 注:プログラミング コードで msoledbsql.lib ファイルを参照する場合、使用しているコンピューターのシステム パス、およびアプリケーションを使用するユーザーのシステム パスに msoledbsql.dll ファイルが含まれることを確認する必要があります。|  

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
