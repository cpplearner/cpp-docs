---
title: "How to: Retrieve Time Elapsed Since Startup (C++-CLI)"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time, elapsed since startup"
  - "counters, elapsed time"
  - "startup, time elapsed since"
  - "tick counts"
  - "startup"
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
caps.latest.revision: 9
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# How to: Retrieve Time Elapsed Since Startup (C++/CLI)
The following code example demonstrates how to determine the tick count, or number of milliseconds that have elapsed since Windows was started. This value is stored in the \<xref:System.Environment.TickCount*?displayProperty=fullName> member and, because it is a 32-bit value, resets to zero approximately every 24.9 days.  
  
## Example  
  
```  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  
  
## See Also  
 [Windows Operations (C++/CLI)](../cli/windows-operations--c---cli-.md)   
 [.NET Programming with C++/CLI (Visual C++)](../cli/.net-programming-with-c---cli--visual-c---.md)