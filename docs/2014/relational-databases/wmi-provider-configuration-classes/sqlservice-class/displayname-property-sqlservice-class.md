---
title: DisplayName プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- DisplayName Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9439b7410821cffe5d959fda7a894e4f69e33ed0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85002323"
---
# <a name="displayname-property-sqlservice-class"></a>DisplayName プロパティ (SqlService クラス)
  サービスの表示名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.DisplayName [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスの表示名を指定する文字列値。  
  
## <a name="remarks"></a>Remarks  
 この文字列の長さは最大 256 文字です。 名前は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで大文字と小文字が区別されます。 ただし、表示名の比較時には、常に大文字と小文字は区別されません。  
  
## <a name="example"></a>例  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
