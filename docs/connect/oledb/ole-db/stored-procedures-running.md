---
title: ストアド プロシージャの実行 (OLE DB) | Microsoft Docs
description: ストアド プロシージャの実行 (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 47b47bade745c8113423678a818a513f962d1cb0
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012745"
---
# <a name="stored-procedures---running"></a>ストアド プロシージャ - 実行
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  ステートメントの実行時、データ ソースに対して (クライアント アプリケーション内で直接ステートメントを実行または準備せずに) ストアド プロシージャを呼び出すと、次のような利点があります。  
  
-   パフォーマンスの向上。  
  
-   ネットワーク オーバーヘッドの軽減。  
  
-   一貫性の向上  
  
-   正確性の向上  
  
-   機能の追加。  
  
 OLE DB Driver for SQL Server は、データを返すために [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャで使用される 3 つのメカニズムをサポートしています。  
  
-   プロシージャ内のすべての SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。  
  
 結果の処理中には、さまざまな OLE DB プロバイダーからさまざまなタイミングで出力パラメーターと戻り値が返されます。 OLE DB Driver for SQL Server の場合、出力パラメーターとリターン コードは、コンシューマーがストアド プロシージャから返された結果セットを取得または取り消すまで提供されません。 これらのリターン コードと出力パラメーターは、サーバーからの最後の TDS パケットで返されます。  
  
 プロバイダーでは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを使用して、出力パラメーターと戻り値を返すタイミングを報告します。 このプロパティは、DBPROPSET_DATASOURCEINFO プロパティ セットに含まれています。  
  
 OLE DB Driver for SQL Server は、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを DBPROPVAL_OA_ATROWRELEASE に設定することにより、結果セットが処理または解放されるまでリターン コードと出力パラメーターが返されないことを示します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ](../../oledb/ole-db/stored-procedures.md)  
  
  
