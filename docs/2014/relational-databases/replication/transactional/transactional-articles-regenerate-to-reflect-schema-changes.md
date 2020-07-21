---
title: カスタム トランザクション プロシージャの再生成によるスキーマ変更の反映 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b41b5309816e037ce3619e880b796e0653c7506
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063704"
---
# <a name="regenerate-custom-transactional-procedures-to-reflect-schema-changes"></a>カスタム トランザクション プロシージャの再生成によるスキーマ変更の反映
  既定では、トランザクション レプリケーションがサブスクライバー上のデータを変更する際、パブリケーション内の各テーブル アーティクルに対して内部プロシージャが生成したストアド プロシージャが必ず使われます。 3 つのプロシージャ (挿入、更新、削除用に 1 つずつ) はサブスクライバーにコピーされ、挿入、更新、削除がサブスクライバーにレプリケートされた時点で実行されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャー上のテーブルでスキーマが変更されると、レプリケーションがスクリプト作成内部プロシージャの同じセットを呼び出すことで、これらのプロシージャが自動的に再生成され、新しいプロシージャと新しいスキーマが一致します (スキーマ変更のレプリケーションは、Oracle パブリッシャーではサポートされていません)。  
  
 カスタム プロシージャを指定して、1 つ以上の既定のプロシージャを置き換えることもできます。 スキーマ変更によってカスタム プロシージャが影響を受ける場合は、そのプロシージャを変更する必要があります。 たとえば、スキーマ変更によって削除される列をプロシージャが参照している場合には、その列への参照をプロシージャから削除する必要があります。 レプリケーションで新しいカスタム プロシージャをサブスクライバーに反映するには、2 つの方法があります。  
  
-   1 つ目のオプションは、カスタム スクリプト作成プロシージャを使用して、レプリケーションで使用する既定のプロシージャを置き換える方法です。  
  
    1.  [Transact-sql&#41;&#40;sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行する場合は、 **@schema_option** 0x02 ビットが**true**であることを確認します。  
  
    2.  [Transact-sql&#41;を実行 sp_register_custom_scripting &#40;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql) 、パラメーターに ' insert '、' update '、または ' delete ' の値を指定し、パラメーターに **@type** カスタムスクリプトプロシージャの名前を指定し **@value** ます。  
  
     次回にスキーマが変更されると、レプリケーションによってこのストアド プロシージャが呼び出され、新しくユーザーが定義したカスタム ストアド プロシージャの定義がスクリプト化されて、プロシージャが各サブスクライバーに反映されます。  
  
-   2 つ目のオプションは、新しいカスタム プロシージャの定義を含むスクリプトを使用する方法です。  
  
    1.  [Transact-sql&#41;&#40;sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行する場合は、 **@schema_option** 0x02 ビットを**false**に設定して、レプリケーションによってカスタムプロシージャがサブスクライバーで自動的に生成されないようにします。  
  
    2.  各スキーマ変更の前に、新しいスクリプト ファイルを作成し、[sp_register_custom_scripting &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql) を実行してスクリプトをレプリケーションに登録します。 パラメーターの値として ' custom_script ' を指定し、 **@type** パラメーターにパブリッシャー上のスクリプトへのパスを指定し **@value** ます。  
  
     次回に関連スキーマが変更されると、各サブスクライバーでは、DDL コマンドと同じトランザクション内でこのスクリプトが実行されます。 スキーマ変更が完了すると、スクリプトの登録が解除されます。 以降のスキーマ変更でこのスクリプトを実行するには、スクリプトを再登録する必要があります。  
  
## <a name="see-also"></a>参照  
 [トランザクションアーティクルに変更を反映する方法を指定します](transactional-articles-specify-how-changes-are-propagated.md)   
 [パブリケーション データベースでのスキーマの変更](../publish/make-schema-changes-on-publication-databases.md)  
  
  
