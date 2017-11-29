---
title: "MMWORD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MMWORD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MMWORD directive"
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# MMWORD
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Wird für Multimedia 64\-Bit\-Operanden mit MMX und XTM \(SSE\) \- Anweisungen.  
  
## Syntax  
  
```  
MMWORD  
```  
  
## Hinweise  
 `MMWORD` ist ein Typ.  Vor MMWORD, das mit MASM hinzugefügt wurde, kann entsprechende Funktionalität erzielt werden mit:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Während beide Anweisungen 64\-Bit\-Operanden arbeiten, ist der Typ für `QWORD` 64\-Bit\-Ganzzahlen ohne Vorzeichen und `MMWORD` ist der Typ für einen Multimedia 64\-Bit\-Wert.  
  
 `MMWORD` muss den gleichen Typ wie [\_\_m64](../../cpp/m64.md)darzustellen.  
  
## Beispiel  
  
```  
movq     mm0, mmword ptr [ebx]  
```