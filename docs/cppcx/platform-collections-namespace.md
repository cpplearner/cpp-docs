---
title: "Platform::Collections Namespace | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.technology: "cpp-windows"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Collections Namespace"
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Platform::Collections Namespace
The Platform::Collection namespace contains the `Map`, `MapView`, `Vector`, and `VectorView` classes. These classes are concrete implementations of the corresponding interfaces that are defined in the [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) namespace. The concrete collection types are not portable across the ABI (for example when a Javascript or C# program calls into a C++ component), but they are implicitly convertible to their corresponding interface types. For example, if you implement a public method that populates and returns a collection, then use [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) to implement the collection internally and use [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) as the return type. For more information, see [Collections](../cppcx/collections-c-cx.md) and [Creating Windows Runtime Components in C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
 You can construct a Platform::Collections::Vector from a [std::vector](../standard-library/vector-class.md) and a [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) from a [std::map](../standard-library/map-class.md).  
  
 In addition, the Platform::Collection namespace provides support for back insert and input iterators, and `Vector` and `VectorView` iterators.  
  
 You must include (`#include`) the collection.h header to use the types in the Platform::Collection namespace.  
  
## Syntax  
  
```cpp  
  
#include <collection.h>  
using namespace Platform::Collection;  
```  
  
### Members  
 This namespace contains the following members.  
  
|Name|Description|  
|----------|-----------------|  
|[Platform::Collections::BackInsertIterator Class](../cppcx/platform-collections-backinsertiterator-class.md)|Represents an iterator that inserts an element at the end of a collection.|  
|[Platform::Collections::InputIterator Class](../cppcx/platform-collections-inputiterator-class.md)|Represents an iterator that inserts an element at the beginning of a collection.|  
|[Platform::Collections::Map Class](../cppcx/platform-collections-map-class.md)|Represents a modifiable collection of key-value pairs that are accessed by a key. Similar to [std::map](../standard-library/map-class.md).|  
|[Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)|Represents a read-only collection of key-value pairs that are accessed by a key.|  
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|Represents a modifiable sequence of elements. Similar to [std::vector](../standard-library/vector-class.md).|  
|[Platform::Collections::VectorIterator Class](../cppcx/platform-collections-vectoriterator-class.md)|Represents an iterator that traverses a `Vector` collection.|  
|[Platform::Collections::VectorView Class](../cppcx/platform-collections-vectorview-class.md)|Represents a read-only sequence of elements.|  
|[Platform::Collections::VectorViewIterator Class](../cppcx/platform-collections-vectorviewiterator-class.md)|Represents an iterator that traverses a `VectorView` collection.|  
  
## Inheritance Hierarchy  
 [Platform namespace](../cppcx/platform-namespace-c-cx.md)  
  
### Requirements  
 **Metadata:** platform.winmd  
  
 **Namespace:** Platform::Collections  
  
 **Compiler option:** /ZW  
  
## See Also  
 [Platform Namespace](../cppcx/platform-namespace-c-cx.md)