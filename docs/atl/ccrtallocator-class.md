---
title: "CCRTAllocator Class"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
f1_keywords: 
  - "CCRTAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTAllocator class"
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: 14
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
# CCRTAllocator Class
This class provides methods for managing memory using CRT memory routines.  
  
## Syntax  
  
```
class ATL::CCRTAllocator
```  
  
## Members  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CCRTAllocator::Allocate](../Topic/CCRTAllocator::Allocate.md)|(Static) Call this method to allocate memory.|  
|[CCRTAllocator::Free](../Topic/CCRTAllocator::Free.md)|(Static) Call this method to free memory.|  
|[CCRTAllocator::Reallocate](../Topic/CCRTAllocator::Reallocate.md)|(Static) Call this method to reallocate memory.|  
  
## Remarks  
 This class is used by [CHeapPtr](../atl/cheapptr-class.md) to provide the CRT memory allocation routines. The counterpart class, [CComAllocator](../atl/ccomallocator-class.md), provides the same methods using COM routines.  
  
## Requirements  
 **Header:** atlcore.h  
  
##  <a name="ccrtallocator__allocate"></a>  CCRTAllocator::Allocate  
 Call this static function to allocate memory.  
  
```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### Parameters  
 `nBytes`  
 The number of bytes to allocate.  
  
### Return Value  
 Returns a void pointer to the allocated space, or NULL if there is insufficient memory available.  
  
### Remarks  
 Allocates memory. See [malloc](../crt/malloc.md) for more details.  
  
##  <a name="ccrtallocator__free"></a>  CCRTAllocator::Free  
 Call this static function to free memory.  
  
```
static void Free(void* p) throw();
```  
  
### Parameters  
 `p`  
 Pointer to the allocated memory.  
  
### Remarks  
 Frees the allocated memory. See [free](../crt/free.md) for more details.  
  
##  <a name="ccrtallocator__reallocate"></a>  CCRTAllocator::Reallocate  
 Call this static function to reallocate memory.  
  
```
static __declspec(allocator) void* Reallocate(
    void*  p,  size_t nBytes) throw();
```  
  
### Parameters  
 `p`  
 Pointer to the allocated memory.  
  
 `nBytes`  
 The number of bytes to reallocate.  
  
### Return Value  
 Returns a void pointer to the allocated space, or NULL if there is insufficient memory.  
  
### Remarks  
 Resizes the amount of allocated memory. See [realloc](../crt/realloc.md) for more details.  
  
## See Also  
 [CHeapPtr Class](../atl/cheapptr-class.md)   
 [CComAllocator Class](../atl/ccomallocator-class.md)   
 [Class Overview](../atl/atl-class-overview.md)
