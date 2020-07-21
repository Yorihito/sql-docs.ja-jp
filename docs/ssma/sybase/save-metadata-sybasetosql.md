---
title: メタデータの保存 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b2517735-dd19-449f-8cee-08e68ca89d3a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 3a8cde296fd0a47c407752977f5e41269a05354e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020969"
---
# <a name="save-metadata--sybasetosql"></a>メタデータの保存 (SybaseToSQL)
[**メタデータの保存**] ダイアログボックスでは、メタデータを保存する前に ssma プロジェクトに読み込むように求めるメッセージが表示されます。 これにより、オフラインで使用したり、技術サポート担当者などの他のユーザーに送信したりできる、完全なプロジェクトファイルを作成できます。  
  
[**メタデータの保存**] ダイアログボックスにアクセスするには、プロジェクトを保存します。 メタデータが見つからない場合は、SSMA によって [**メタデータの保存**] ダイアログボックスが表示されます。  
  
## <a name="options"></a>Options  
**名前**  
プロジェクト内の各データベースの名前。  
  
**状態**  
メタデータが SSMA プロジェクトに読み込まれるかどうか、またはメタデータが存在しないかどうかを示します。  
  
SSMA は、必要に応じてメタデータをプロジェクトに読み込みます。 メタデータを参照し、スキーマを変換すると、メタデータが自動的に読み込まれます。  
  
**すべて選択**  
一覧表示されているすべてのデータベースを選択します。  
  
**クリア**  
メタデータが欠落しているすべてのデータベースのチェックボックスをオフにします。 メタデータが読み込まれている場合は、このチェックボックスをオフにすることはできません。  
  
**および**  
プロジェクトを保存し、メタデータが存在しない選択したデータベースのメタデータを読み込みます。  
  
**キャンセル**  
保存操作をキャンセルします。 見つからないメタデータはプロジェクトに読み込まれません。  
  
