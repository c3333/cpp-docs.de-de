---
title: "ComPtr::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::Reset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Gibt alle Verweise für den Zeiger auf die Schnittstelle an, die diesem ComPtr zugeordnet ist.  
  
## Syntax  
  
```  
unsigned long Reset();  
```  
  
## Rückgabewert  
 Die Anzahl der freigegeben Verweise, sofern vorhanden.  
  
## Anforderungen  
 **Header:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## Siehe auch  
 [ComPtr\-Klasse](../windows/comptr-class.md)