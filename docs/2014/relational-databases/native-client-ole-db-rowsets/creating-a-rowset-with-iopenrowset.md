---
title: IOpenRowset を使用した行セットの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055988"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>IOpenRowset を使用した行セットの作成
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、 **IOpenRowset:: OpenRowset**メソッドがサポートされていますが、次の制限があります。  
  
-   *pTableID* パラメーターが指すデータベース ID (DBID) 構造体に、ベース テーブルまたはビューを指定する必要があります。  
  
-   DBID の *eKind* メンバーに DBKIND_NAME を指定する必要があります。  
  
-   DBID の *uName* メンバーには、既存のベース テーブルまたはビューの名前を Unicode 文字列で指定する必要があります。  
  
-   **OpenRowset** の *pIndexID* パラメーターには NULL を指定する必要があります。  
  
 **IOpenRowset::OpenRowset** の結果セットには、1 つの行セットが含まれます。 1つの行セットを含む結果セットは、カーソルでサポートでき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 開発者はカーソル サポートによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンカレンシー メカニズムを使用できます。  
  
## <a name="see-also"></a>参照  
 [行セット](rowsets.md)  
  
  
