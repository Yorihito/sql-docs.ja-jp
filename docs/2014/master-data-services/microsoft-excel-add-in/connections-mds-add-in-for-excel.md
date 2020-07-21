---
title: 接続 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1704cf87bfebf0cab80630f3dcb66517b0f5420a
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961422"
---
# <a name="connections-mds-add-in-for-excel"></a>接続 (Excel 用 MDS アドイン)
  データを [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]にダウンロードするには、まず接続を作成する必要があります。 接続とは、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスがどの MDS データベースに接続するかを認識する方法です。  
  
 通常、接続文字列は [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL (http://contoso/mds など) です。  
  
 Excel を起動するたびに、MDS リポジトリに接続する必要があります。 ただし、アクティブなワークシートに MDS によって管理されるデータが既に含まれている場合だけは例外です。 この場合は、シート内のデータを更新またはパブリッシュするたびに接続が自動的に確立されます。  
  
 接続は複数作成することができます。 最後にアクセスした接続が既定と見なされます。  
  
 複数のユーザーが同時に接続できます。 ただし、複数のユーザーが同じデータをパブリッシュしようとすると競合が発生する可能性があります。 詳細については、「[データ &#40;Excel 用 MDS アドイン&#41;のパブリッシュ](overview-importing-data-from-excel-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>自動接続とよく使用するデータの読み込み  
 常に同じサーバーに接続して同じデータ セットを読み込む場合は、接続およびフィルター情報を含むショートカット クエリ ファイルを作成できます。 クエリ ファイルの詳細については、「 [ショートカット クエリ ファイル (Excel 用 MDS アドイン)](shortcut-query-files-mds-add-in-for-excel.md)をクリックします。  
  
## <a name="data-quality-services"></a>Data Quality Services  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] には、MDS リポジトリにパブリッシュする前にデータを照合するための Data Quality Services 機能が用意されています。 接続時に、DQS データベースが MDS データベースと同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにインストールされている場合は、リボンに DQS ボタンが表示されます。 DQS_Main データベースがインスタンスに存在しない場合、DQS ボタンは表示されず、データ品質機能を使用することはできません。  
  
## <a name="troubleshooting-connections"></a>接続のトラブルシューティング  
 MDS に接続するときに問題が発生した場合は、「 [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) トラブルシューティングのヒント」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースへの接続を作成します。|[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|MDS データを Excel に読み込みます。|[MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)|  
|Excel に読み込む前に MDS データをフィルター処理します。|[&#40;Excel 用 MDS アドインを読み込む前にデータをフィルター処理する&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [データ &#40;Excel 用 MDS アドインの読み込み&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [ショートカット クエリ ファイル (Excel 用 MDS アドイン)](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Microsoft Excel 用マスター データ サービス アドイン](master-data-services-add-in-for-microsoft-excel.md)  
  
  
