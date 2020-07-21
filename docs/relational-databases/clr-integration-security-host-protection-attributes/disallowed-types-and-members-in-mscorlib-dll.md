---
title: mscorlib.dll | で許可されていない型とメンバーMicrosoft Docs
description: SQL Server CLR プログラミングでは、HostProtectionResource 列挙型の値を持つ型またはメンバーを使用できません。 この記事では、許可されていない値 mscorlib.dll 一覧を示します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: daf82d4b-2f6d-44ca-9148-75193321b6d5
author: rothja
ms.author: jroth
ms.openlocfilehash: d57e0cba6a0bb12d62b73ff6e064196a8d89c452
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727733"
---
# <a name="disallowed-types-and-members-in-mscorlibdll"></a>mscorlib.dll の許可されない型およびメンバー
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語統合 (CLR) プログラミングでは、 **Hostprotectionattribute**が指定されている型またはメンバーの使用を禁止しています。これは**externalprocessmgmt**、 **externalスレッディング**、 **MayLeakOnAbort**、 **securityinfrastructure**、 **SelfAffectingProcessMgmnt**、 **SelfAffectingThreading**、 **Sharedstate**、 **Synchronization**、または**UI**の値を持つ、 **hostprotectionattribute**列挙体を指定します。 次の表は、ホスト保護属性 (HPA) 値が許可されない mscorlib.dll アセンブリのメンバーおよび型を示しています。  
  
> [!NOTE]  
>  この一覧は、サポートされているアセンブリから作成されたものです。 詳細については、「[サポートされている .NET Framework ライブラリ](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。  
  
|型またはメンバー|HPA 値|  
|--------------------|--------------------|  
|SyncStream.BeginRead()|ExternalThreading|  
|SyncStream.BeginWrite()|ExternalThreading|  
|System.Collections.ArrayList.Synchronized()|同期|  
|System.Collections.Hashtable.Synchronized()|同期|  
|System.Collections.Queue.Synchronized()|同期|  
|System.Collections.SortedList.Synchronized()|同期|  
|System.Collections.Stack.Synchronized()|同期|  
|System.Console.Beep()|UI|  
|System.Console.get_Error()|UI|  
|System.Console.get_In()|UI|  
|System.Console.get_KeyAvailable()|UI|  
|System.Console.get_Out()|UI|  
|System.Console.OpenStandardError()|UI|  
|System.Console.OpenStandardInput()|UI|  
|System.Console.OpenStandardOutput()|UI|  
|System.Console.Read()|UI|  
|System.Console.ReadKey()|UI|  
|System.Console.ReadLine()|UI|  
|System.Console.SetError()|UI|  
|System.Console.SetIn()|UI|  
|System.Console.SetOut()|UI|  
|System.Console.Write()|UI|  
|System.Console.WriteLine()|UI|  
|System.Diagnostics.LogMessageEventHandler|ExternalThreading、Synchronization|  
|System.IO.FileStream.BeginRead()|ExternalThreading|  
|System.IO.FileStream.BeginWrite()|ExternalThreading|  
|System.IO.Stream.Synchronized()|同期|  
|System.IO.TextReader.Synchronized()|同期|  
|System.IO.TextWriter.Synchronized()|同期|  
|System.Reflection.Emit.AssemblyBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.ConstructorBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.CustomAttributeBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.EnumBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.EventBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.FieldBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.MethodBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.MethodRental|MayLeakOnAbort|  
|System.Reflection.Emit.ModuleBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.PropertyBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.TypeBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.UnmanagedMarshal|MayLeakOnAbort|  
|System.Security.Principal.WindowsPrincipal|SecurityInfrastructure|  
|System.Threading.AutoResetEvent|ExternalThreading、Synchronization|  
|System.Threading.EventWaitHandle|ExternalThreading、Synchronization|  
|System.Threading.ManualResetEvent|ExternalThreading、Synchronization|  
|System.Threading.Monitor|ExternalThreading、Synchronization|  
|System.Threading.Mutex|ExternalThreading、Synchronization|  
|System.Threading.ReaderWriterLock|ExternalThreading、Synchronization|  
|System.Threading.Thread.AllocateDataSlot()|ExternalThreading、SharedState|  
|System.Threading.Thread.AllocateNamedDataSlot()|ExternalThreading、SharedState|  
|System.Threading.Thread.BeginCriticalRegion()|ExternalThreading、Synchronization|  
|System.Threading.Thread.EndCriticalRegion()|ExternalThreading、Synchronization|  
|System.Threading.Thread.FreeNamedDataSlot()|ExternalThreading、SharedState|  
|System.Threading.Thread.GetData()|ExternalThreading、SharedState|  
|System.Threading.Thread.GetNamedDataSlot()|ExternalThreading、SharedState|  
|System.Threading.Thread.Join()|ExternalThreading、Synchronization|  
|System.Threading.Thread.set_ApartmentState()|Synchronization、SelfAffectingThreading|  
|System.Threading.Thread.set_CurrentUICulture()|ExternalThreading|  
|System.Threading.Thread.set_IsBackground()|SelfAffectingThreading|  
|System.Threading.Thread.set_Name()|ExternalThreading|  
|System.Threading.Thread.set_Priority()|SelfAffectingThreading|  
|System.Threading.Thread.SetApartmentState()|Synchronization、SelfAffectingThreading|  
|System.Threading.Thread.SetData()|ExternalThreading、SharedState|  
|System.Threading.Thread.SpinWait()|ExternalThreading、Synchronization|  
|System.Threading.Thread.Start()|ExternalThreading、Synchronization|  
|System.Threading.Thread.TrySetApartmentState()|Synchronization、SelfAffectingThreading|  
|System.Threading.ThreadPool|ExternalThreading、Synchronization|  
|System.Threading.Timer|ExternalThreading、Synchronization|  
|System.Threading.TimerBase|ExternalThreading、Synchronization|  
  
## <a name="see-also"></a>関連項目  
 [ホスト保護属性と CLR 統合プログラミング](../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Microsoft.VisualBasic.dllで許可されていない型とメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [System.dllで許可されていない型とメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)   
 [System.Data.dllで許可されていない型とメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)   
 [System.Core.dll の許可されない型およびメンバー](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
  
  
