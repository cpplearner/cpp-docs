---
title: "CDocItem Class"
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
  - "CDocItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "items, document"
  - "document items"
  - "server documents, document items"
  - "CDocItem class"
  - "container document items"
  - "client document items"
  - "OLE documents, items"
  - "server documents"
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: 19
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
# CDocItem Class
The base class for document items, which are components of a document's data.  
  
## Syntax  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## Members  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CDocItem::GetDocument](#cdocitem__getdocument)|Returns the document that contains the item.|  
|[CDocItem::IsBlank](#cdocitem__isblank)|Determines whether the item contains any information.|  
  
## Remarks  
 `CDocItem` objects are used to represent OLE items in both client and server documents.  
  
 For more information, see the article [Containers: Implementing a Container](../mfc/containers--implementing-a-container.md).  
  
## Inheritance Hierarchy  
 [CObject](../mfcref/cobject-class.md)  
  
 [CCmdTarget](../mfcref/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## Requirements  
 **Header:** afxole.h  
  
##  <a name="cdocitem__getdocument"></a>  CDocItem::GetDocument  
 Call this function to get the document that contains the item.  
  
```  
CDocument* GetDocument() const;  
```  
  
### Return Value  
 A pointer to the document that contains the item; **NULL**, if the item is not part of a document.  
  
### Remarks  
 This function is overridden in the derived classes [COleClientItem](../mfcref/coleclientitem-class.md) and [COleServerItem](../mfcref/coleserveritem-class.md), returning a pointer to either a [COleDocument](../mfcref/coledocument-class.md), a [COleLinkingDoc](../mfcref/colelinkingdoc-class.md), or a [COleServerDoc](../mfcref/coleserverdoc-class.md) object.  
  
##  <a name="cdocitem__isblank"></a>  CDocItem::IsBlank  
 Called by the framework when default serialization occurs.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### Return Value  
 Nonzero if the item contains no information; otherwise 0.  
  
### Remarks  
 By default, `CDocItem` objects are not blank. [COleClientItem](../mfcref/coleclientitem-class.md) objects are sometimes blank because they derive directly from `CDocItem`. However, [COleServerItem](../mfcref/coleserveritem-class.md) objects are always blank. By default, OLE applications containing `COleClientItem` objects that have no x or y extent are serialized. This is done by returning **TRUE** from an override of `IsBlank` when the item has no x or y extent.  
  
 Override this function if you want to implement other actions during serialization.  
  
## See Also  
 [CCmdTarget Class](../mfcref/ccmdtarget-class.md)   
 [Hierarchy Chart](../mfc/hierarchy-chart.md)   
 [COleDocument Class](../mfcref/coledocument-class.md)   
 [COleServerItem Class](../mfcref/coleserveritem-class.md)   
 [COleClientItem Class](../mfcref/coleclientitem-class.md)