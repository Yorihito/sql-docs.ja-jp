---
title: valueOf (java.sql.Timestamp, java.util.Calendar) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41234033feda27a48aa9f2c8d3cf573926db8c50
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919465"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>valueOf (java.sql.Timestamp, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  引数に java.sql.Timestamp 値とオフセットを示す java.util.Calendar 値を受け取って、GMT からの特定のオフセットで特定の時点を表す **DateTimeOffset** オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *timestamp*  
  
 java.sql.Timestamp値です。  
  
 *カレンダー*  
  
 オフセットの値。  *calendar* の日付と時刻の要素は、*timestamp* 値に従って設定されます。  
  
## <a name="return-value"></a>戻り値  
 特定の java.util.Calendar オブジェクトのタイム ゾーンで java.sql.Timestamp オブジェクトで指定された特定の時点を表す DateTimeOffset オブジェクトを返します。  
  
## <a name="remarks"></a>解説  
 また、このメソッドは、java.util.Calendar オブジェクトを java.sql.Timestamp オブジェクトで指定された特定の時点に設定します。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
