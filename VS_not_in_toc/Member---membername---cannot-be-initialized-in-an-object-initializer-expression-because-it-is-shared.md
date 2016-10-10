---
title: "Member &#39;&lt;membername&gt;&#39; cannot be initialized in an object initializer expression because it is shared"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
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
# Member &#39;&lt;membername&gt;&#39; cannot be initialized in an object initializer expression because it is shared
Object initializers cannot be used to initialize any member of a class that is declared as shared. For more information, see [Shared](../Topic/Shared%20\(Visual%20Basic\).md).  
  
 **Error ID:** BC30991  
  
### To correct this error  
  
1.  Examine the class definition to determine which member is shared.  
  
2.  Eliminate the initialization for that member from the object initializer list.  
  
## Example  
 In the following example, `totalCustomers` is a shared member.  
  
```  
Public Class Customer  
    Public Shared totalCustomers As Integer  
    ' Other declarations and method definitions.  
End Class  
```  
  
 Because `totalCustomers` is shared, trying to set its initial value in an object initializer list causes this error.  
  
```  
' This declaration is not valid.  
' Dim cust As New Customer With { .Name = "Coho Winery", _  
'                                 .totalCustomers = 21 }  
```  
  
## See Also  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)   
 [NOT IN BUILD: Shared Members in Visual Basic](assetId:///dbc3783f-83a2-4225-995d-c2d6d025663d)