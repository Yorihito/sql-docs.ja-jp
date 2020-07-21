---
title: Command オブジェクト (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command
helpviewer_keywords:
- Command object [ADO]
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f6b2e68947959ecd497645d2290bb7acaa03f86
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760410"
---
# <a name="command-object-ado"></a>Command オブジェクト (ADO)
データソースに対して実行する特定のコマンドを定義します。  
  
## <a name="remarks"></a>解説  
 **コマンド**オブジェクトを使用して、データベースに対してクエリを実行し、レコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトのレコードを返します。また、一括操作を実行したり、データベースの構造を操作したりします。 プロバイダーの機能によっては、**コマンド**のコレクション、メソッド、またはプロパティによっては、参照時にエラーが発生することがあります。  
  
 **Command**オブジェクトのコレクション、メソッド、およびプロパティを使用して、次の操作を実行できます。  
  
-   [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティを使用して、コマンドの実行可能テキスト (たとえば、SQL ステートメント) を定義します。 また、単純な文字列以外のコマンドまたはクエリ構造 (XML テンプレートクエリなど) の場合は、 [Commandstream](../../../ado/reference/ado-api/commandstream-property-ado.md)プロパティを使用してコマンドを定義します。  
  
-   必要に応じて、 **CommandText**プロパティと**commandstream**で使用されるコマンド[の言語](../../../ado/reference/ado-api/dialect-property.md)を指定します。  
  
-   [パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトと[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションを使用して、パラメーター化クエリまたはストアドプロシージャ引数を定義します。  
  
-   [Namedparameters](../../../ado/reference/ado-api/namedparameters-property-ado.md)プロパティを使用して、プロバイダーにパラメーター名を渡す必要があるかどうかを示します。  
  
-   [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドに該当する場合は、コマンドを実行し、**レコードセット**オブジェクトを返します。  
  
-   パフォーマンスを最適化するには、実行前に[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティを使用してコマンドの種類を指定します。  
  
-   [準備されたプロパティを](../../../ado/reference/ado-api/prepared-property-ado.md)使用して、準備済み (またはコンパイル済み) のコマンドを実行前に保存するかどうかを制御します。  
  
-   [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)プロパティを使用して、コマンドの実行をプロバイダーが待機する秒数を設定します。  
  
-   [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティを設定して、開いている接続を**Command**オブジェクトに関連付けます。  
  
-   [Name](../../../ado/reference/ado-api/name-property-ado.md)プロパティを設定して、関連付けられている[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトのメソッドとして**コマンド**オブジェクトを識別します。  
  
-   データを取得するために、**レコードセット**の[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)プロパティに**Command**オブジェクトを渡します。  
  
-   [プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、プロバイダー固有の属性にアクセスします。  
  
> [!NOTE]
>  **Command**オブジェクトを使用せずにクエリを実行するには、**接続**オブジェクトの[Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッド、または**レコードセット**オブジェクトの[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドにクエリ文字列を渡します。 ただし、コマンドのテキストを永続化して再実行する場合、またはクエリパラメーターを使用する場合は、 **command**オブジェクトが必要です。  
  
 以前に定義した**接続**オブジェクトとは別に**Command**オブジェクトを作成するには、 **ActiveConnection**プロパティを有効な接続文字列に設定します。 ADO は**接続**オブジェクトを作成しますが、そのオブジェクトをオブジェクト変数に割り当てません。 ただし、複数の**Command**オブジェクトを同じ接続に関連付ける場合は、**接続**オブジェクトを明示的に作成して開く必要があります。これにより、**接続**オブジェクトがオブジェクト変数に割り当てられます。 **Connection**オブジェクトを**Command**オブジェクトの**ActiveConnection**プロパティに割り当てる前に、正常に開かれたことを確認してください。閉じた**接続**オブジェクトを割り当てるとエラーが発生します。 **Command**オブジェクトの**ActiveConnection**プロパティをこのオブジェクト変数に設定しなかった場合、同じ接続文字列を使用していても、ADO によって**コマンド**オブジェクトごとに新しい**接続**オブジェクトが作成されます。  
  
 コマンドを実行するには、関連付けられている**接続**オブジェクトの[Name](../../../ado/reference/ado-api/name-property-ado.md)プロパティを使って**コマンド**を呼び出します。 **コマンド**の**ActiveConnection**プロパティが**接続**オブジェクトに設定されている必要があります。 **コマンド**にパラメーターがある場合は、その値を引数としてメソッドに渡します。  
  
 同じ接続で2つ以上の**command**オブジェクトが実行され、いずれかの**command**オブジェクトが出力パラメーターを持つストアドプロシージャである場合、エラーが発生します。 各**コマンド**オブジェクトを実行するには、別の接続を使用するか、接続から他のすべての**コマンド**オブジェクトを切断します。  
  
 **Parameters**コレクションは、 **Command**オブジェクトの既定のメンバーです。 その結果、次の2つのコードステートメントは等価です。  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   **コマンド**オブジェクトは、スクリプト作成には安全ではありません。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Command オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
