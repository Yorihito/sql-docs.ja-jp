---
title: サブジェクト代替名を使用するように Reporting Services を構成する | Microsoft Docs
description: rsreportserver.config ファイルを変更し、Netsh.exe ツールを使用することで、SAN を使用するように SQL Server Reporting Services を構成する方法について説明します。
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ecb4b0be06731070c0852f23375fafea0eed4434
ms.sourcegitcommit: 66a0672e47415dbd5cfd8d19075102c8c3973e70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83767062"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>サブジェクト代替名を使用するように Reporting Services を構成する

このトピックでは、rsreportserver.config ファイルを変更し、Netsh.exe ツールを使用することによって、サブジェクト代替名 (SAN) を使用するように Reporting Services (SSRS) を構成する方法について説明します。

この手順は、レポート サービスの URL および Web サービス URL に適用されます。

SAN を使用するには、TLS/SSL 証明書がサーバーに登録され、署名され、秘密キーを保持している必要があります。 自己署名証明書は使用できません  
  
 TLS/SSL 証明書を使用するように、Reporting Services の URL を構成できます。 通常、証明書にはサブジェクト名のみが記載されているため、トランスポート層セキュリティ (TLS) (旧称 Secure Sockets Layer (SSL)) セッションに対して許可される URL は 1 つだけです。 SAN は証明書の追加フィールドであり、それにより、TLS サービスでは、さまざまな URL を待ち受け、TLS ポートを他のアプリケーションと共有することができるます。 SAN は `www.s2.com` のようになります。  
  
 Reporting Services の TLS 設定の詳細については、「[ネイティブ モードのレポート サーバーでの TLS 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>サブジェクト代替名を Web サービス URL に使用するように SSRS を構成する
  
1.  Reporting Services 構成マネージャーを開始します。  
  
     詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
2.  **[Web サービス URL]** ページで、TLS/SSL ポートおよび TLS/SSL 証明書を選択します。  
  
     ![Reporting Services 構成マネージャー](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Reporting Services 構成マネージャー")  
  
     構成マネージャーによって、ポート用の TLS/SSL 証明書が登録されます。  
  
3.  rsreportserver.config ファイルを開きます。  
  
     SSRS ネイティブ モードの場合、ファイルは、既定では、次のフォルダーにあります。  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  レポート サーバー Web サービス アプリケーションの URL セクションをコピーします。  
  
     元の URL セクションの例:  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     変更後の URL セクション:
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  rsreportserver.config ファイルを保存します。  
  
6.  管理者としてコマンド プロンプトを起動し、Netsh.exe ツールを実行します。  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  次のように入力して、http コンテキストに切り替えます。  
  
    ```  
    Netsh>http  
    ```  
  
8.  次のように入力して、既存の urlacl を表示します。
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     次のようなエントリが表示されます。  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     urlacl は、予約された URL の DACL (任意のアクセス制御リスト) です。  
  
9. 次のように入力して、既存のエントリと同じユーザーおよび SDDL を持つ、サブジェクト代替名の新しいエントリを作成します。  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. Reporting Services 構成マネージャーの **[レポート サーバーの状態]** ページで、 **[停止]** をクリックしてから **[開始]** をクリックし、レポート サーバーを再起動します。  
  
## <a name="see-also"></a>関連項目

 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services 構成マネージャー](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services の構成ファイルの変更](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [レポート サーバーの URL の構成](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
