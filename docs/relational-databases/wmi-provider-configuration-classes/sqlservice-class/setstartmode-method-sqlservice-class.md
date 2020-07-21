---
title: SetStartMode メソッド (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 15cfa1eddcd9a32b51984d3833c288fc006d395b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888354"
---
# <a name="setstartmode-method-sqlservice-class"></a>SetStartMode メソッド (SqlService クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  サービス インスタンスの開始モードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *StartMode*  
 サービスインスタンスの開始モードを指定する**uint32**値。  
  
 有効な値は次のとおりです。  
  
 値 = 0。 (Boot)。デバイス ドライバーがオペレーティング システム ローダーによって開始されます。 この値は、ドライバー サービスに対してのみ指定できます。  
  
 値 = 1。 システムデバイスドライバーが**Ioinitsystem**メソッドによって開始されました。 この値は、ドライバー サービスに対してのみ指定できます。  
  
 値 = 2。 (Automatic)。システムの起動時に、サービス コントロール マネージャーによってサービスが自動的に開始されます。  
  
 値 = 3。 Manual-プロセスが**startservice**メソッドを呼び出すときに、コンピューターマネージャーによって開始されるサービス。  
  
 値 = 4。 (Disabled)。サービスを開始できません。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **Uint32**値。サービスが正常に変更された場合は0、要求がサポートされていない場合は1になります。 それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
