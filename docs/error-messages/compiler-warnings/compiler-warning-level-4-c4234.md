---
title: "Compilerwarnung (Stufe 4) C4234 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4234"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4234"
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Compilerwarnung (Stufe 4) C4234
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Nicht dem Standard entsprechende Erweiterung: Schlüsselwort 'Schlüsselwort' ist für zukünftige Versionen reserviert  
  
 Der Compiler ist noch nicht in der Lage, das von Ihnen verwendete Schlüsselwort zu implementieren.  
  
 Diese Warnung wird automatisch zu einem Fehler heraufgestuft.  Um dieses Verhalten zu ändern, verwenden Sie [\#pragma warning](../../preprocessor/warning.md).  Um C4234 beispielsweise in eine Warnung der Stufe 4 umzuwandeln, verwenden Sie  
  
```  
#pragma warning(2:4234)  
```  
  
 in der Quellcodedatei.