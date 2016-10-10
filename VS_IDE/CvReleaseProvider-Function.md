---
title: "CvReleaseProvider Function"
ms.custom: na
ms.date: 10/03/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-ide-debug
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
manager: ghogen
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
# CvReleaseProvider Function
Releases marker provider. Releasing the marker provider will not affect previously created marker series of this provider. Marker series have to be release separately by CvReleaseMarkerSeries call. Failure to release provider causes a memory leak.  
  
## Syntax  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### Parameters  
 `pProvider`  
 Provider context. Cannot be NULL.  
  
## Return Value  
 S_OK when provider is successfully released or error code in case there were any errors. Use SUCCEEDED/FAILED macros to check for error condition.  
  
## Requirements  
 **Header:** cvmarkers.h  
  
## See Also  
 [C++ Library Reference](../VS_IDE/C---Library-Reference.md)