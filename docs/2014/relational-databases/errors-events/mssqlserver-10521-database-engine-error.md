---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c034bd13e212b9b39bfd348353d59e23fc748079
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968152"
---
# <a name="mssqlserver_10521"></a>MSSQLSERVER_10521
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10521|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_PARAM_NEEDED|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。'%ls' として指定した `@type` のパラメーターが NULL です。 この型のパラメーターには、NULL 以外の値を指定する必要があります。 NULL 以外の値をパラメーターに指定するか、パラメーターに NULL 値を指定可能な型に変更します。|  
  
## <a name="explanation"></a>説明  
 `@type` で指定した型のパラメーターには、NULL 以外の値を指定する必要がありますが、NULL 値を指定しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 NULL 以外の値をパラメーターに指定するか、パラメーターに NULL 値を指定可能な型に変更します。  
  
## <a name="see-also"></a>参照  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
