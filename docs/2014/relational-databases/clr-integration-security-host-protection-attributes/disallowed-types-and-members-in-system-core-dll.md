---
title: Interdit les Types et membres dans System.Core.dll | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: dcd24cd6-f4ab-42cc-9786-a1604e8a4b4e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f078caae791e4009a309e7cc70d7af333ca4c90f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919562"
---
# <a name="disallowed-types-and-members-in-systemcoredll"></a>Types et membres interdits dans System.Core.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmation de l’intégration (CLR) langage commun n’autorise pas l’utilisation d’un type ou membre qui a un `HostProtectionAttribute` qui spécifie un `System.Security.Permissions.HostProtectionResource` énumération avec la valeur `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, ou `UI`. Le tableau suivant répertorie les membres et les types des assemblys System.Core.dll dont les valeurs d'attribut de protection de l'hôte (HPA) sont interdites.  
  
> [!NOTE]  
>  Cette liste a été générée à partir des assemblys pris en charge. Pour plus d’informations, consultez [prise en charge des bibliothèques .NET Framework](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Type ou membre|Valeur(s) HPA|  
|--------------------|--------------------|  
|System.Diagnostics.Eventing.EventDescriptor|MayLeakOnAbort|  
|System.Diagnostics.Eventing.EventProvider|MayLeakOnAbort|  
|System.Diagnostics.Eventing.EventProviderTraceListener|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementEntityAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.WmiConfigurationAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementMemberAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementNewInstanceAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementBindAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementCreateAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementRemoveAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementEnumeratorAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementProbeAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementTaskAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementKeyAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementReferenceAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementConfigurationAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementCommitAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.ManagementNameAttribute|MayLeakOnAbort|  
|System.Management.Instrumentation.InstrumentationBaseException|MayLeakOnAbort|  
|System.Management.Instrumentation.InstrumentationException|MayLeakOnAbort|  
|System.Management.Instrumentation.InstanceNotFoundException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventBookmark|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogConfiguration|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogLink|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogStatus|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventProperty|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogPropertySelector|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventRecord|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventKeyword|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLevel|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogRecord|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogReader|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogWatcher|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventRecordWrittenEventArgs|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogSession|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventMetadata|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventOpcode|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventTask|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogNotFoundException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogReadingException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogProviderDisabledException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogInvalidDataException|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.EventLogInformation|MayLeakOnAbort|  
|System.Diagnostics.Eventing.Reader.ProviderMetadata|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptHandle|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle|MayLeakOnAbort|  
|System.Security.Cryptography.Aes|MayLeakOnAbort|  
|System.Security.Cryptography.AesCryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.AesManaged|MayLeakOnAbort|  
|System.Security.Cryptography.CngAlgorithm|MayLeakOnAbort|  
|System.Security.Cryptography.CngAlgorithmGroup|MayLeakOnAbort|  
|System.Security.Cryptography.CngKey|MayLeakOnAbort|  
|System.Security.Cryptography.CngKeyBlobFormat|MayLeakOnAbort|  
|System.Security.Cryptography.CngKeyCreationParameters|MayLeakOnAbort|  
|System.Security.Cryptography.CngProperty|MayLeakOnAbort|  
|System.Security.Cryptography.CngPropertyCollection|MayLeakOnAbort|  
|System.Security.Cryptography.CngProvider|MayLeakOnAbort|  
|System.Security.Cryptography.CngUIPolicy|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellman|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellmanPublicKey|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellmanCng|MayLeakOnAbort|  
|System.Security.Cryptography.ECDiffieHellmanCngPublicKey|MayLeakOnAbort|  
|System.Security.Cryptography.ECDsa|MayLeakOnAbort|  
|System.Security.Cryptography.ECDsaCng|MayLeakOnAbort|  
|System.Security.Cryptography.ManifestSignatureInformation|MayLeakOnAbort|  
|System.Security.Cryptography.ManifestSignatureInformationCollection|MayLeakOnAbort|  
|System.Security.Cryptography.MD5Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA1Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA256Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA256CryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.SHA384Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA384CryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.SHA512Cng|MayLeakOnAbort|  
|System.Security.Cryptography.SHA512CryptoServiceProvider|MayLeakOnAbort|  
|System.Security.Cryptography.StrongNameSignatureInformation|MayLeakOnAbort|  
|System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation|MayLeakOnAbort|  
|System.Security.Cryptography.X509Certificates.TimestampInformation|MayLeakOnAbort|  
|Microsoft.Win32.SafeHandles.SafePipeHandle|MayLeakOnAbort|  
|System.TimeZoneInfo|MayLeakOnAbort|  
|System.TimeZoneNotFoundException|MayLeakOnAbort|  
|System.InvalidTimeZoneException|MayLeakOnAbort|  
|System.Diagnostics.EventSchemaTraceListener|MayLeakOnAbort|  
|System.Diagnostics.UnescapedXmlDiagnosticData|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterData|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterSetInstanceCounterDataSet|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterSet|MayLeakOnAbort|  
|System.Diagnostics.PerformanceData.CounterSetInstance|MayLeakOnAbort|  
|System.Collections.Generic.HashSet`1|MayLeakOnAbort|  
|System.IO.Pipes.PipeStream|MayLeakOnAbort|  
|System.IO.Pipes.AnonymousPipeServerStream|MayLeakOnAbort|  
|System.IO.Pipes.AnonymousPipeClientStream|MayLeakOnAbort|  
|System.IO.Pipes.NamedPipeServerStream|MayLeakOnAbort|  
|System.IO.Pipes.NamedPipeClientStream|MayLeakOnAbort|  
|System.IO.Pipes.PipeAccessRule|MayLeakOnAbort|  
|System.IO.Pipes.PipeAuditRule|MayLeakOnAbort|  
|System.IO.Pipes.PipeSecurity|MayLeakOnAbort|  
|System.Threading.LockRecursionException|MayLeakOnAbort|  
|System.Threading.ReaderWriterLockSlim|MayLeakOnAbort|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de Protection hôte et programmation de l’intégration CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Types et membres dans Microsoft.VisualBasic.dll interdits](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Types et membres dans mscorlib.dll interdits](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Types et membres dans System.dll interdits](disallowed-types-and-members-in-system-dll.md)   
 [Types et membres non autorisés dans System.Data.dll](disallowed-types-and-members-in-system-data-dll.md)  
  
  
