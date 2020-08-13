---
title: データ型の処理 (JDBC)
description: これらのサンプル アプリケーションから JDBC Driver for SQL Server のデータ型を操作する方法について学習します。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6994e7ce587cf72d7879c79604cbe3c68873ddf0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923286"
---
# <a name="working-with-data-types-jdbc"></a>データ型の処理 (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] の主な機能は、Java 開発者が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに含まれたデータにアクセスできるようにすることです。 これを可能にするために、JDBC ドライバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型と Java 言語の型やオブジェクトとの間の変換を仲介します。

> [!NOTE]
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および JDBC ドライバーのデータ型について、その相違点や Java 言語のデータ型への変換方法など、詳細については、「[JDBC ドライバーのデータ型について](understanding-the-jdbc-driver-data-types.md)」を参照してください。

SQL Server のデータ型を処理するために、JDBC ドライバーには、[SQLServerPreparedStatement](reference/sqlserverpreparedstatement-class.md) および [SQLServerCallableStatement](reference/sqlservercallablestatement-class.md) クラスに get\<Type> および set\<Type> メソッドがあり、[SQLServerResultSet](reference/sqlserverresultset-class.md) クラスに get\<Type> および update\<Type> メソッドがあります。 使用するメソッドは、処理するデータの型と、結果セットまたはクエリを使用するかどうかによって決まります。

このセクションのトピックでは、JDBC ドライバーのデータ型を使用して Java アプリケーションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データにアクセスする方法について説明します。

## <a name="in-this-section"></a>このセクションの内容

|トピック|説明|
|-----------|-----------------|
|[基本データ型のサンプル](basic-data-types-sample.md)|結果セットの getter メソッドを使用して基本的な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の値を取得する方法と、結果セットの update メソッドを使用してそれらの値を更新する方法を示しています。|
|[SQLXML データ型のサンプル](sqlxml-data-type-sample.md)|XML データのリレーショナル データベースへの格納、データベースからの XML データの取得、および、XML データの解析を、**SQLXML** Java データ型を使用して行う方法を示しています。|
|[空間データ型のサンプル](spatial-data-types-sample.md)|Microsoft JDBC Driver によって定義されている **Geometry** および **Geography** Java 型を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの空間データ型 'Geometry' と 'Geography' を使用して、データを格納および取得する方法について説明します。|

## <a name="see-also"></a>関連項目

[サンプル JDBC ドライバー アプリケーション](sample-jdbc-driver-applications.md)
