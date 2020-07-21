---
title: IBCPSession::BCPColFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f8cbd2789fbf4f941642439545f7c8fa349cf66
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048041"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a>IBCPSession::BCPColFmt (OLE DB)
  プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a>Remarks  
 **BCPColFmt** メソッドは、BCP データ ファイルのフィールドと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成するために使用します。 このメソッドは、列の長さ、型、ターミネータ、およびプレフィックス長をパラメーターとして受け取り、個々のフィールドの対応するプロパティに設定します。  
  
 ユーザーが対話モードを選択すると、このメソッドが 2 回呼び出されます。1 回は既定値 (サーバーの列の型によって異なります) に応じて列形式を設定するために呼び出され、もう 1 回はクライアントが対話モードで選択した列の型に応じて各列の形式を設定するために呼び出されます。  
  
 対話モード以外の場合、このメソッドは列ごとに 1 回だけ呼び出され、各列の型を文字型またはネイティブ型に設定し、列ターミネータと行ターミネータを設定します。  
  
 **BCPColFmt** メソッドにより、一括コピーのユーザー ファイル形式を指定できます。 次に、一括コピーに使用するフォーマットの内容を示します。  
  
-   ユーザー ファイルのフィールドからデータベース列へのマッピング  
  
-   ユーザー ファイルの各フィールドのデータ型  
  
-   各フィールドの省略可能なインジケーターの長さ  
  
-   ユーザー ファイルの各フィールドにおけるデータの最大長  
  
-   各フィールドの省略可能なターミネータ バイト シーケンス  
  
-   省略可能なターミネータ バイト シーケンスの長さ  
  
 **BCPColFmt** を呼び出すたびに、ユーザー ファイルの 1 つのフィールドの形式が指定されます。 たとえば、5 つのフィールドから構成されるユーザー データ ファイルの 3 つのフィールドの既定の設定を変更するには、まず、`BCPColumns(5)` を呼び出し、**BCPColFmt** を 5 回呼び出します。この 5 回の呼び出しのうち 3 回は独自の形式を設定して呼び出します。 残りの 2 回の呼び出しでは、*eUserDataType* を BCP_TYPE_DEFAULT に設定し、*cbIndicator*、*cbUserData*、*cbUserDataTerm* をそれぞれ 0、BCP_VARIABLE_LENGTH、0 に設定します。 このプロシージャでは、5 つの列すべてをコピーします。それらの列のうち 3 つはカスタマイズされた形式でコピーされ、2 つは既定の形式でコピーされます。  
  
> [!NOTE]  
>  **BCPColFmt** を呼び出す前に、[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) メソッドを呼び出す必要があります。 **BCPColFmt** は、ユーザー ファイル内の列ごとに 1 回呼び出す必要があります。 **BCPColFmt** をユーザー ファイルの任意の列に対して複数回呼び出すと、エラーが発生します。  
  
 ユーザー ファイル内の全データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにコピーする必要はありません。 列をスキップするには、列のデータの形式を指定する際に idxServerCol パラメーターを 0 に設定します。 一方、フィールドをスキップする場合は、メソッドを正しく機能させるためにすべての情報が必要になります。  
  
 **注**[IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 関数を使用すると、**BCPColFmt** で指定された形式指定を保存できます。  
  
## <a name="arguments"></a>引数  
 *idxUserDataCol*[in]  
 ユーザー データ ファイル内のフィールドのインデックス。  
  
 *eUserDataType*[in]  
 ユーザー データ ファイル内のフィールドのデータ型。 使用できるデータ型は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ヘッダーファイル (sqlncli) に、BCP_TYPE_SQLINT4 などの BCP_TYPE_XXX 形式で一覧表示されます。 BCP_TYPE_DEFAULT 値を指定すると、プロバイダーはテーブルやビューの列と同じ型を使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `eUserDataType` 引数が BCP_TYPE_SQLDECIMAL または BCP_TYPE_SQLNUMERIC の場合に、ファイル内で一括コピー操作を実行するには、次のようにします。  
  
-   コピー元の列が decimal 型または numeric 型以外の場合は、既定の有効桁数と小数点以下桁数が使用されます。  
  
-   コピー元の列が decimal 型または numeric 型の場合は、コピー元の列の有効桁数と小数点以下桁数が使用されます。  
  
 *cbIndicator*[in]  
 フィールドのプレフィックス長。 既定値は BCP_PREFIX_DEFAULT です。 有効なプレフィックス長は、0、1、2、4、および 8 です。 フィールドがチャンク分割される場合に頻繁に使用されるプレフィックスのサイズは 8 です。 チャンク分割は、大きい値になっている列を効率的に一括コピーするために使用します。  
  
 *cbUserData*[in]  
 ユーザー ファイル内にあるフィールド データの最大長 (バイト単位)。長さのインジケーターやターミネータの長さは含まれません。  
  
 `cbUserData`を BCP_LENGTH_NULL に設定すると、データファイルのフィールドのすべての値がであるか、NULL に設定される必要があることを示します。 `cbUserData`を BCP_LENGTH_VARIABLE に設定すると、各フィールドのデータの長さがシステムによって決定されることになります。 これは、フィールドによっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーされるデータの前に長さのインジケーターや NULL インジケーターを生成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするデータにインジケーターが必要になる場合があることを意味します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字データ型およびバイナリデータ型の場合、には `cbUserData` BCP_LENGTH_VARIABLE、BCP_LENGTH_NULL、0、または正の値を指定できます。 が BCP_LENGTH_VARIABLE の場合、 `cbUserData` システムは長さインジケーター (存在する場合) またはターミネータシーケンスを使用してデータの長さを決定します。 長さのインジケーターとターミネータ シーケンスの両方を指定した場合、一括コピーはコピーするデータ量が少なくなる方法を使用します。 `cbUserData`が BCP_LENGTH_VARIABLE の場合、データ型は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字型またはバイナリ型です。長さのインジケーターもターミネータシーケンスも指定されていない場合、システムはエラーメッセージを返します。  
  
 `cbUserData`が0または正の値の場合、システムは `cbUserData` 最大データ長としてを使用します。 ただし、正の `cbUserData` 長さのインジケーターまたはターミネータシーケンスが指定されている場合、システムは、コピーされるデータ量が最小になるメソッドを使用してデータ長を決定します。  
  
 値は、 `cbUserData` データのバイト数を表します。 文字データが Unicode ワイド文字で表されている場合、正の `cbUserData` パラメーター値は、各文字のサイズ (バイト単位) を乗算した文字数を表します。  
  
 *pbUserDataTerm*[size_is][in]  
 フィールドに使用するターミネータ シーケンス。 このパラメーターは主に文字データ型に対して有効です。これは、他のすべての型は固定長であったり、バイト数を正確に記録するために長さのインジケーターが必要になる (バイナリ データの場合) ためです。  
  
 抽出されるデータが途中で終了されないようにしたり、ユーザー ファイル内のデータが途中で終了していないことを示すには、このパラメーターに NULL を設定します。  
  
 複数の方法 (ターミネータと長さのインジケーター、ターミネータと列の最大長など) を使用してユーザー ファイルの列長を指定すると、一括コピーはコピーするデータの量が最も少なくなる方法を使用します。  
  
 一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。 このため、ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定するように注意する必要があります。  
  
 *cbUserDataTerm*[in]  
 列に使用するターミネータ シーケンスの長さ (バイト単位)。 データ内にターミネータが存在しないか不要な場合は、この値を 0 に設定します。  
  
 *idxServerCol*[in]  
 データベース テーブル内での列の序数位置。 最初の列の序数は 1 です。 列の序数位置は **IColumnsInfo::GetColumnInfo** などのメソッドから報告されます。 この値が 0 の場合、一括コピーではデータ ファイル内のこのフィールドは無視されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、このメソッドが呼び出される前に、[IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) メソッドが呼び出されなかった場合などです。  
  
 E_INVALIDARG  
 引数が無効です。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)  
  
  
