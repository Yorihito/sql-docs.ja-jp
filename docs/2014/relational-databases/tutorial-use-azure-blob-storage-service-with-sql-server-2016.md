---
title: 'チュートリアル: Azure Storage サービスでのデータファイルの SQL Server |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b80b6af9b198db61f8cd34360ddbb3e00bc13d7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85037200"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a>チュートリアル:Azure Storage サービス内の SQL Server データ ファイル
  Azure Storage サービスでのデータファイルの SQL Server に関するチュートリアルへようこそ。 このチュートリアルを読むと、Azure Blob Storage サービスに SQL Server データ ファイルを直接格納する方法がわかります。  
  
 Azure Blob ストレージサービスの SQL Server 統合サポートは、SQL Server 2014 の拡張機能です。 この機能を使用する場合の機能と利点の概要については、「 [Azure でのデータファイルの SQL Server](databases/sql-server-data-files-in-microsoft-azure.md)」を参照してください。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、複数のレッスンで Azure Storage サービスに SQL Server データファイルを格納する方法について説明します。 各レッスンでは特定のタスクに重点を置きます。 まず、Azure でストレージアカウントとコンテナーを作成する方法について説明します。 次に、SQL Server を Azure Storage と統合できるように SQL Server 資格情報を作成する方法について説明します。 次に、Azure Storage でデータベースを直接作成します。 さらに、暗号化、移行、およびバックアップと復元のシナリオを示します。  
  
 このチュートリアルは、次の 9 つのレッスンで構成されています。  
  
 **[レッスン 1:Azure Storage アカウントとコンテナーを作成する](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 このレッスンでは、Azure Storage アカウントとコンテナーを作成します。  
  
 **[レッスン2。コンテナーでポリシーを作成し、SAS&#41; キー &#40;Shared Access Signature を生成する](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 このレッスンでは、BLOB コンテナーのポリシーを作成し、Shared Access Signature を生成します。  
  
 **[レッスン 3:SQL Server 資格情報の作成](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 このレッスンでは、Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
 **[レッスン 4:Azure Storage にデータベースを作成する](../relational-databases/lesson-3-database-backup-to-url.md)**  
 このレッスンでは、CREATE Database FILENAME オプションを使用して Azure Storage でデータベースを作成します。  
  
 **[レッスン 5.&#40;オプション&#41; TDE を使用してデータベースを暗号化する](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 このレッスンでは、透過的なデータ暗号化 (TDE) およびサーバー証明書を使用してデータベースを暗号化します。  
  
 **[レッスン 6: オンプレミスのソース コンピューターから Azure のターゲット コンピューターにデータベースを移行する](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 このレッスンでは、CREATE DATABASE FOR ATTACH オプションを使用して、オンプレミスから Azure の仮想マシンにデータベースを移行します。  
  
 **[レッスン 7: Azure Storage にデータ ファイルを移動する](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 このレッスンでは、ALTER DATABASE ステートメントを使用して、データファイルを Azure Storage に移動します。  
  
 **[レッスン8。Azure Storage にデータベースを復元する](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 このレッスンでは、RESTORE Database MOVE オプションを使用して Azure Storage するようにデータベースを復元します。  
  
 **[レッスン 9.Azure Storage からデータベースを復元する](lesson-8-restore-as-new-database-from-log-backup.md)**  
 このレッスンでは、RESTORE Database MOVE オプションを使用して Azure Storage からデータベースを復元します。  
  
## <a name="see-also"></a>参照  
 [Azure でのデータファイルの SQL Server](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
