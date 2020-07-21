---
title: Open メソッド (ADO Record) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: rothja
ms.author: jroth
ms.openlocfilehash: 723d42cda8ac741f697dec7be4a2c4f5ad662508
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762193"
---
# <a name="open-method-ado-record"></a>Open メソッド (ADO Record)
既存の[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトを開くか、ファイルやディレクトリなどの**レコード**によって表される新しい項目を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 任意。 この**レコード**オブジェクトによって表されるエンティティの URL、**コマンド**、開いているレコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)または別の**レコード**オブジェクト、SQL SELECT ステートメントまたはテーブル名を含む文字列を表す**バリアント**。  
  
 *ActiveConnection*  
 任意。 接続文字列または開いている[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトを表す**バリアント**です。  
  
 *モード*  
 任意。 結果の**レコード**オブジェクトのアクセスモードを指定する[connectmodeenum](../../../ado/reference/ado-api/connectmodeenum.md)値です。 既定値は**Admodeunknown**です。  
  
 *CreateOptions*  
 任意。 既存のファイルまたはディレクトリを開くか、新しいファイルまたはディレクトリを作成する必要があるかを指定する[Recordcreateoptionsenum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)値。 既定値は**Adfailifnotexists**です。 既定値に設定されている場合、アクセスモードは[mode](../../../ado/reference/ado-api/mode-property-ado.md)プロパティから取得されます。 *Source*パラメーターに URL が含まれていない場合、このパラメーターは無視されます。  
  
 *[オプション]*  
 任意。 **レコード**を開くためのオプションを指定する[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)値です。 既定値は**Adopenrecordunspecified**です。 これらの値は組み合わせることができます。  
  
 *ユーザー名*  
 任意。 必要に応じて、*ソース*へのアクセスを承認するユーザー ID を表す**文字列**値です。  
  
 *パスワード*  
 任意。 必要に応じて*ユーザー名*を確認するパスワードを含む**文字列**値です。  
  
## <a name="remarks"></a>解説  
 *ソース*は次のようになります。  
  
-   URL。 URL のプロトコルが http の場合、インターネットプロバイダーが既定で呼び出されます。 URL が、のような実行可能スクリプトを含むノードを指している場合は。ASP ページ) 既定では、実行されたコンテンツではなく、ソースを含む**レコード**が開かれます。 この動作を変更するには、 *Options*引数を使用します。  
  
-   **レコード**オブジェクト。 別の**レコード**から開かれた**レコード**オブジェクトは、元の**レコード**オブジェクトを複製します。  
  
-   **コマンド**オブジェクト。 開いている**レコード**オブジェクトは、**コマンド**の実行によって返される単一行を表します。 結果に1つ以上の行が含まれている場合は、最初の行の内容がレコードに配置され **、エラーがエラーコレクションに**追加されることがあります。  
  
-   SQL SELECT ステートメント。 開いている**レコード**オブジェクトは、文字列の内容を実行して返される単一行を表します。 結果に1つ以上の行が含まれている場合は、最初の行の内容がレコードに配置され **、エラーがエラーコレクションに**追加されることがあります。  
  
-   テーブル名。  
  
 **レコード**オブジェクトが、URL を使用してアクセスできないエンティティ (たとえば、データベースから派生した**レコードセット**の行) を表している場合、 [parenturl](../../../ado/reference/ado-api/parenturl-property-ado.md)プロパティと**adRecordURL**定数でアクセスされるフィールドの両方の値は null になります。  
  
> [!NOTE]
>  Http スキームを使用する Url は、[インターネット公開のために Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)を自動的に呼び出します。 詳細については、「[絶対 url と相対 url](../../../ado/guide/data/absolute-and-relative-urls.md)」を参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)
