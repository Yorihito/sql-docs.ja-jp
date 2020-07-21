---
title: フルテキストカタログ名の長さは、120文字に制限されます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fa9b06fa6fe4acd79782c19a8814357721e59c24
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045209"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>フルテキスト カタログ名が最長 120 文字に制限されている
  フルテキスト カタログ名の長さが 120 文字に制限されており、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における最大長 (128 文字) より文字数が少なくなっています。  
  
## <a name="description"></a>説明  
 この変更は既存のカタログ名には影響しません。ただし、120 文字よりも長い名前を持つフルテキスト カタログを作成するスクリプトはエラーになります。 カタログ名は、カタログに対応する論理ファイル名の生成に使用されます。  
  
## <a name="corrective-action"></a>修正措置  
 フルテキスト カタログを作成するすべてのスクリプトを変更し、カタログ名を 120 文字までにします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
