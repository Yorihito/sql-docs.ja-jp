---
title: パラメーター化されたコマンドと介在する COMPUTE コマンド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f66bde29a5036ed671f9af17bf5aab1df4acbca
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764783"
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>介在する COMPUTE コマンドを含むパラメーター化されたコマンド
一般的なパラメーター化された shape APPEND コマンドには、クエリコマンドを使用して親**レコードセット**を作成する句と、パラメーター化されたクエリコマンドを使用して子**レコードセット**を作成する句があります。これは、パラメーターのプレースホルダー (疑問符 "?") を含むコマンドです。 結果の整形された**レコードセット**には、親が上位レベルを占め、子が下位レベルを占める2つのレベルがあります。  
  
 子**レコードセット**を作成する句は、任意の数の入れ子になった shape COMPUTE コマンドにすることができます。この場合、最も深い入れ子になったコマンドにはパラメーター化クエリが含まれます。 結果の整形された**レコードセット**には複数のレベルがあり、親は最上位レベルを占め、子は lowermost レベルを占有し、shape COMPUTE コマンドによって生成される任意の数の**レコードセット**が、介在するレベルを占有します。  
  
 この機能の一般的な用途は、shapeCOMPUTE コマンドの集計関数とグループ化の機能を呼び出して、子**レコードセット**に関する分析情報を含む中間**レコードセット**オブジェクトを作成することです。 さらに、これはパラメーター化された shape コマンドであるため、親のチャプター列にアクセスするたびに、新しい子**レコードセット**が取得される場合があります。 介在するレベルは子から派生しているので、再計算されます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
