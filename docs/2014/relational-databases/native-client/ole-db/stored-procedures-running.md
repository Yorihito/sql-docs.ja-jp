---
title: ストアド プロシージャの実行 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: rothja
ms.author: jroth
ms.openlocfilehash: 786101d76185c21763787ab11fd29600938be198
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055809"
---
# <a name="running-stored-procedures-ole-db"></a>ストアド プロシージャの実行 (OLE DB)
  ステートメントの実行時、データ ソースに対して (クライアント アプリケーション内で直接ステートメントを実行または準備せずに) ストアド プロシージャを呼び出すと、次のような利点があります。  
  
-   パフォーマンスの向上。  
  
-   ネットワーク オーバーヘッドの軽減。  
  
-   一貫性の向上  
  
-   正確性の向上  
  
-   機能の追加。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアドプロシージャがデータを返すために使用する3つのメカニズムがサポートされています。  
  
-   プロシージャ内のすべての SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。  
  
 結果の処理中には、さまざまな OLE DB プロバイダーからさまざまなタイミングで出力パラメーターと戻り値が返されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの場合、ストアドプロシージャによって返された結果セットをコンシューマーが取得またはキャンセルするまで、出力パラメーターとリターンコードは提供されません。 これらのリターン コードと出力パラメーターは、サーバーからの最後の TDS パケットで返されます。  
  
 プロバイダーでは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを使用して、出力パラメーターと戻り値を返すタイミングを報告します。 このプロパティは、DBPROPSET_DATASOURCEINFO プロパティ セットに含まれています。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを DBPROPVAL_OA_ATROWRELEASE に設定して、結果セットが処理または解放されるまでリターンコードと出力パラメーターが返されないことを示します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ](stored-procedures.md)  
  
  
