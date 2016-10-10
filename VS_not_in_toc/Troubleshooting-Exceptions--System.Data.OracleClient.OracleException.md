---
title: "Troubleshooting Exceptions: System.Data.OracleClient.OracleException"
ms.custom: na
ms.date: 10/02/2016
ms.devlang: 
  - JScript
  - VB
  - CSharp
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
manager: douge
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# Troubleshooting Exceptions: System.Data.OracleClient.OracleException
An <xref:System.Data.OracleClient.OracleException?qualifyHint=False> exception is generated when a warning or error is returned by an Oracle database or the .NET Framework Data Provider for Oracle.  
  
## Associated Tips  
 **Verify that you are connecting with valid credentials.**  
 Make sure that the credentials you are supplying are valid.  
  
 **Verify that the server name is correct and that the server is running.**  
 Make sure that you are using the correct server name, and that the server can be reached.  
  
## Remarks  
 This exception is thrown whenever the <xref:System.Data.OracleClient.OracleDataAdapter?qualifyHint=False> encounters an error generated by the server.  
  
 If the severity of the error is too great, the server may close the <xref:System.Data.OracleClient.OracleConnection?qualifyHint=False>. However, the user can reopen the connection and continue.  
  
## See Also  
 <xref:System.Data.OracleClient.OracleException?qualifyHint=False>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)