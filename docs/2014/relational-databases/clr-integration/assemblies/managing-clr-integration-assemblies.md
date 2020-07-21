---
title: CLR 統合アセンブリの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: f9acc56d72d2ed994f497676813e45ef0a914431
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953782"
---
# <a name="managing-clr-integration-assemblies"></a>CLR 統合アセンブリの管理
  マネージド コードは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。 アセンブリは DLL ファイルまたは実行可能 (.exe) ファイルとしてパッケージ化されます。 実行可能ファイルが単独で実行できるのに対し、DLL は既存のアプリケーションでホストする必要があります。 マネージ DLL アセンブリは、に読み込んでホストすることができ [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] ます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]CREATE ASSEMBLY ステートメントを使用して、データベースをプロセスに読み込み、使用する前に使用します。 アセンブリは、ALTER ASSEMBLY ステートメントを使用してより最近のバージョンから更新することも、DROP ASSEMBLY ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から削除することも可能です。  
  
 アセンブリ情報は、アセンブリがインストールされているデータベース内の `sys.assembly_files` テーブルに格納されます。 `sys.assembly_files` テーブルには、次の列が含まれています。  
  
|列|説明|  
|------------|-----------------|  
|assembly_id|アセンブリに定義される ID。 この番号は、同じアセンブリに関連するすべてのオブジェクトに割り当てられます。|  
|name|オブジェクトの名前。|  
|file_id|各オブジェクトを識別する番号。最初のオブジェクトは、値 1 が割り当てられている所定の `assembly_id` に関連付けられます。 複数のオブジェクトが同じ `assembly_id` に関連付けられている場合、その後に続く各 `file_id` 値は 1 ずつ増加します。|  
|コンテンツ|アセンブリまたはファイルの 16 進数表記。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アセンブリの作成](creating-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における SAFE、EXTERNAL_ACCESS、および UNSAFE CLR アセンブリの作成について説明します。  
  
 [アセンブリの変更](altering-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における CLR アセンブリの更新について説明します。  
  
 [アセンブリの削除](dropping-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からの CLR アセンブリの削除について説明します。  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](../security/clr-integration-security.md)   
 [CLR 統合のコード アクセス セキュリティ](../security/clr-integration-code-access-security.md)  
  
  
