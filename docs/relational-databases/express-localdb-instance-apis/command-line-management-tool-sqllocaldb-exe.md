---
title: 'コマンドライン管理ツール: SqlLocalDB.exe |Microsoft Docs'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c39272a1f8af7fce092f7aa31ac3a4f7ebd2263
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765251"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>コマンド ライン管理ツール: SqlLocalDB.exe
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  SqlLocalDB.exe は、コマンド ラインから LocalDB インスタンスを簡単に管理できるシンプルなツールです。 LocalDB インスタンスの API の単純なラッパーとして実装されています。 SQLCMD などの多くの SQL Server ツールの場合と同様、パラメーターはコマンド ライン引数として SqlLocalDB に渡され、出力はコンソールに送られます。  
  
 SqlLocalDB では、開発者が LocalDB を使用できます。API を呼び出すコードを記述したり、他のツールを使用したりする必要はありません。  
  
## <a name="sqllocaldb-options"></a>SqlLocalDB オプション  
 SqlLocalDB では、次のオプションがサポートされています。  
  
|オプション|実行内容|  
|------------|------------------|  
|`-?`|ヘルプ テキストを出力します。|  
|`create\|c "instance name" [version-number] [-s]`|指定された名前とバージョンで LocalDB インスタンスを新規作成します。<br /><br /> [version-number] パラメーターを省略した場合、既定で SqlLocalDB ビルド バージョンになります。<br /><br /> -s は、LocalDB インスタンスの新規作成後に、そのインスタンスを起動します。|  
|`delete\|d "instance name"`|指定した名前の LocalDB インスタンスを削除します。|  
|`start\|s "instance name"`|指定した名前の LocalDB インスタンスを起動します。|  
|`stop\|p "instance name" [-i\|-k]`|現在のクエリの実行が終了した後、指定した名前の LocalDB インスタンスを停止します。<br /><br /> -i は、NOWAIT オプション付きで LocalDB インスタンスのシャットダウンを要求します。<br /><br /> -k は、LocalDB インスタンス プロセスに通知することなく、そのプロセスを停止します。|  
|`share\|h ["owner SID or account"] "private name" "shared name"`|指定された共有名を使用して、指定されたプライベート インスタンスを共有します。 ユーザー SID またはアカウント名を省略した場合、既定で現在のユーザーになります。|  
|`unshare\|u "shared name"`|指定された共有 LocalDB インスタンスの共有を解除します。|  
|`info\|i`|現在のユーザーが所有している既存のすべての LocalDB インスタンス、および共有されているすべての LocalDB インスタンスを一覧表示します。|  
|`info\|i "instance name"`|指定された LocalDB インスタンスに関する情報を出力します。|  
|`versions\|v`|コンピューターにインストールされているすべての LocalDB バージョンを一覧表示します。|  
|||  
|`trace\|t on\|off`|トレースのオンとオフを切り替えます。|  
  
 SqlLocalDB では、スペースを区切り文字として扱います。スペースと特殊文字が含まれるインスタンス名は、引用符で囲む必要があります。 次に例を示します。  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
