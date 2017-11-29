---
title: "Linkertoolwarnung LNK4001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4001"
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Linkertoolwarnung LNK4001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Keine Objektdateien angegeben; Bibliotheken werden verwendet  
  
 An den Linker wurden eine oder mehrere LIB\-Dateien, aber keine OBJ\-Dateien übergeben.  
  
 Da der Linker nicht in der Lage ist, in einer LIB\-Datei auf dieselben Informationen zuzugreifen wie in einer OBJ\-Datei, weist diese Warnung darauf hin, dass Sie explizit andere Linkeroptionen angeben müssen.  Unter Umständen müssen Sie z. B. die Optionen [\/MACHINE](../../build/reference/machine-specify-target-platform.md), [\/OUT](../../build/reference/out-output-file-name.md) oder [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) angeben.