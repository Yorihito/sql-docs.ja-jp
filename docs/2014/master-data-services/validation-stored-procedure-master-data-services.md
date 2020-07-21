---
title: 検証ストアド プロシージャ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 976892ce912cc2eeded2ea9b470b9ce338ff6a8f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970915"
---
# <a name="validation-stored-procedure-master-data-services"></a>検証ストアド プロシージャ (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールをモデル バージョンのすべてのメンバーに適用するためにバージョンが検証されます。  
  
 このトピックでは、 **mdm.udpValidateModel** ストアド プロシージャを使用してデータを検証する方法について説明します。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションの管理者であれば、代わりに UI で検証を実行することができます。 詳細については、「 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](validate-a-version-against-business-rules-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  ステージング処理が完了する前に検証を呼び出すと、ステージングが終了していないメンバーは検証されません。  
  
## <a name="example"></a>例  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>パラメーター  
 このプロシージャのパラメーターを次に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|UserID|ユーザー ID。|  
|Model_ID|モデル ID。|  
|Version_ID|バージョン ID。|  
  
## <a name="see-also"></a>参照  
 [データのインポート &#40;マスターデータサービス&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](validate-a-version-against-business-rules-master-data-services.md)  
  
  
