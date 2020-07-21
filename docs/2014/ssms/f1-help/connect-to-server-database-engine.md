---
title: '[サーバーへの接続] (データベース エンジン) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc7281dab01d97df3608825a4e51c256f1b5296c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064441"
---
# <a name="connect-to-server-database-engine"></a>[サーバーへの接続] (データベース エンジン)
  このダイアログを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] に接続するときのオプションを表示または指定できます。 ほとんどの場合、 **[サーバー名]** ボックスにデータベース サーバーのコンピューター名を入力し、 **[接続]** をクリックすることで接続できます。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]に接続している場合、コンピューター名の後に **\sqlexpress**を付けて使用します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続する機能に影響する要因は多数あります。  
  
## <a name="options"></a>Options  
 **サーバーの種類**  
 オブジェクト エクスプローラーからサーバーを登録するときは、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、または [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]) を選択します。 ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。 [登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。 別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde-md.md)]]、[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]]、[ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]]、[ [!INCLUDE[ssEW](../../includes/ssew-md.md)]]、または [ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ] をクリックします。  
  
 **サーバー名**  
 接続するサーバー インスタンスを選択します。 既定では、最後に接続していたサーバー インスタンスが表示されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のアクティブなユーザー インスタンスに接続するには、パイプ名を指定した名前付きパイプ プロトコル (np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query など) を使用して接続します。詳細については、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のドキュメントを参照してください。  
  
 **認証**  
 のインスタンスに接続するときに、2つの認証モードを使用でき [!INCLUDE[ssDE](../../includes/ssde-md.md)] ます。  
  
 **Windows 認証モード ([Windows 認証])**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。  
  
 **SQL Server 認証**  
 指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。  
  
 **ユーザー名**  
 接続に使用するユーザー名を入力します。 このオプションは、Windows 認証を使用した接続を選択した場合のみ使用できます。  
  
 **Login**  
 接続に使用するログインを入力します。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続が指定されている場合にのみ使用できます。  
  
 **パスワード**  
 ログインのパスワードを入力します。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合のみ編集できます。  
  
 **接続する**  
 クリックすると、上記で選択したサーバーに接続します。  
  
 **Options**  
 クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。  
  
  
