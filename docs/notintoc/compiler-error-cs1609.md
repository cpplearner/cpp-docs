---
title: "Compiler Error CS1609"
ms.custom: na
ms.date: "10/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "CS1609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1609"
ms.assetid: 89e112f8-6337-4803-8741-2e38497deb8c
caps.latest.revision: 11
ms.author: "billchi"
manager: "douge"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# Compiler Error CS1609
Modifiers cannot be placed on event accessor declarations  
  
 Modifiers can only be placed on event declarations and not on the event accessor declarations. For more information, see [Using Properties](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Example  
 The following sample generates CS1609.  
  
```  
// CS1609.cs  
// compile with: /target:library  
delegate int Del();  
class A  
{  
   public event Del MyEvent   
   {  
      private add {}   // CS1609  
      // try the following line instead  
      // add {}  
      remove {}  
   }  
}  
```