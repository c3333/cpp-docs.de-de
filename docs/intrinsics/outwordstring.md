---
title: "__outwordstring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep outsw-Anweisung"
  - "__outwordstring intrinsic"
  - "outsw-Anweisung"
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __outwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft\-spezifisch**  
  
 Generiert die `rep outsw`\-Anweisung, die `Count` Wörter sendet, die bei `Buffer` den E\/A\-Port beginnen, der von `Port`angegeben wird.  
  
## Syntax  
  
```  
void __outwordstring(   
   unsigned short Port,   
   unsigned short* Buffer,   
   unsigned long Count   
);  
```  
  
#### Parameter  
 \[in\] `Port`  
 Der Anschluss, um die Daten zu senden.  
  
 \[in\] `Buffer`  
 Ein Zeiger auf die Daten werden ausgesendet, den angegebenen Anschluss.  
  
 \[in\] `Count`  
 Die Anzahl der zu sendenden den Wörtern.  
  
## Anforderungen  
  
|Intrinsisch|Architektur|  
|-----------------|-----------------|  
|`__outwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Headerdatei** \<intrin.h\>  
  
## Hinweise  
 Diese Routine ist als systeminterne Funktion nur verfügbar.  
  
## Microsoft ENDES bestimmten  
  
## Siehe auch  
 [Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)