---
title: データベースエンジンの構成-Filestream |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012731"
---
# <a name="database-engine-configuration---filestream"></a>データベース エンジンの構成 - Filestream
  このページを使用すると、このインストールの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に対して FILESTREAM を有効にすることができます。 FILESTREAM は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] `varbinary(max)` バイナリラージオブジェクト (BLOB) データをファイルシステム上のファイルとして格納することにより、と NTFS ファイルシステムを統合します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、FILESTREAM データの挿入、更新、クエリ、検索、およびバックアップを行うことができます。 Win32 ファイル システム インターフェイスによるデータへのストリーミング アクセスが可能になります。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 **[Transact-SQL アクセスに対して FILESTREAM を有効にする]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする場合にオンにします。 他のコントロール オプションを使用できるようにするには、先にこのコントロールをオンにする必要があります。  
  
 **[ファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]**  
 FILESTREAM の Win32 ストリーム アクセスを有効にする場合にオンにします。  
  
 **[Windows 共有名]**  
 このコントロールは、FILESTREAM データを格納する Windows 共有の名前を入力する場合に使用します。  
  
 **[リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]**  
 このコントロールは、リモート クライアントにこのサーバー上のこの FILESTREAM データへのアクセスを許可する場合にオンにします。  
  
## <a name="see-also"></a>参照  
 [FILESTREAM の有効化と構成](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
