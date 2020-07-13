---
title: GenerateDatabaseRightsScript メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 575eab878e0ef9b4357c09a0a3deedf143c237b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098480"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a>GenerateDatabaseRightsScript メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー データベースおよびレポート サーバーの実行に必要なその他のデータベースに対してユーザー権限を付与する際に使用できる、SQL スクリプトを生成します。 呼び出し元は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース サーバーに接続して、スクリプトを実行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *UserName*  
 スクリプトで権限を与えるユーザーのユーザー名または Windows セキュリティ識別子 (SID)。  
  
 *DatabaseName*  
 スクリプトによってユーザーにアクセス権が付与されるデータベース名。  
  
 *IsRemote*  
 データベースがレポート サーバーに対してリモートであるかどうかを示すブール値。  
  
 *IsWindowsUser*  
 指定されたユーザー名が Windows ユーザーか [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーかを示すブール値。  
  
 *[スクリプト]*  
 [out] 生成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプトを含む文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>解説  
 *DatabaseName* が空の場合、 *IsRemote* は無視され、レポート サーバーの構成ファイルの値がデータベース名に使用されます。  
  
 *Iswindowsuser*がに`true`設定されている場合、*ユーザー名*はドメイン\\><\>username の形式\<である必要があります。  
  
 *Iswindowsuser*がに`true`設定されている場合、生成されたスクリプトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のユーザーにログイン権限を与え、レポートサーバーデータベースを既定のデータベースとして設定し、レポートサーバーデータベース、レポートサーバー一時データベース、master データベース、および MSDB システムデータベースに対して**RSExec**ロールを付与します。  
  
 *Iswindowsuser*がに`true`設定されている場合、メソッドは標準の Windows sid を入力として受け入れます。 標準 Windows SID またはサービス アカウント名が指定されると、ユーザー名文字列に変換されます。 データベースがローカルである場合、アカウントはアカウントのローカライズされた正しい表現に変換されます。 データベースがリモートである場合、アカウントはコンピューターのアカウントとして表されます。  
  
 次の表は、変換されるアカウントとそのリモート表現を示しています。  
  
|変換されるアカウントまたは SID|共通名|リモート名|  
|---------------------------------------|-----------------|-----------------|  
|(S-1-5-18)|[ローカル システム]|\<Domain>\\<ComputerName\>$|  
|.\LocalSystem|[ローカル システム]|\<Domain>\\<ComputerName\>$|  
|ComputerName\LocalSystem|[ローカル システム]|\<Domain>\\<ComputerName\>$|  
|LocalSystem|[ローカル システム]|\<Domain>\\<ComputerName\>$|  
|(S-1-5-20)|Network Service|\<Domain>\\<ComputerName\>$|  
|NT AUTHORITY\NetworkService|Network Service|\<Domain>\\<ComputerName\>$|  
|(S-1-5-19)|Local Service|エラー - 下記参照。|  
|NT AUTHORITY\LocalService|Local Service|エラー - 下記参照。|  
  
 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]では、組み込みアカウントを使用し、レポート サーバー データベースがリモートである場合、エラーが返されます。  
  
 `LocalService` 組み込みアカウントを指定し、レポート サーバー データベースがリモートである場合、エラーが返されます。  
  
 *IsWindowsUser* が true であり、 *UserName* に指定した値を変換する必要がある場合、WMI プロバイダーはレポート サーバー データベースが同じコンピューターにあるかリモート コンピューターにあるかを確認します。 インストールがローカルであるかどうかを確認するため、WMI プロバイダーは以下の値一覧に対して DatabaseServerName プロパティを評価します。 一致が見つかった場合、データベースはローカルです。 見つからなかった場合、リモートです。 比較では大文字と小文字は区別されません。  
  
|DatabaseServerName の値|例|  
|---------------------------------|-------------|  
|"."||  
|"(local)"||  
|"LOCAL"||  
|localhost||  
|\<Machinename>|testlab14|  
|\<MachineFQDN>|example.redmond.microsoft.com|  
|\<IPAddress>|180.012.345,678|  
  
 *Iswindowsuser*がに`true`設定されている場合、WMI プロバイダーは LookupAccountName を呼び出してアカウントの SID を取得し、lookupaccountsid 関数を呼び出して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スクリプトに含める名前を取得します。 このようにすると、使用するアカウント名は必ず [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 検証に合格します。  
  
 *Iswindowsuser*がに`false`設定されている場合、生成されたスクリプトによって、レポートサーバーデータベース、レポートサーバー一時データベース、および MSDB データベースの**RSExec**ロールが付与されます。  
  
 *Iswindowsuser*がに`false`設定されている場合、スクリプトを正常に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行するには、SQL Server ユーザーがに既に存在している必要があります。  
  
 レポート サーバーにレポート サーバー データベースが指定されていない場合、GrantRightsToDatabaseUser を呼び出すとエラーが返されます。  
  
 生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
