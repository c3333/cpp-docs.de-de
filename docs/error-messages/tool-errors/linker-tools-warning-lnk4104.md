---
title: "Linkertoolwarnung LNK4104 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4104"
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Linkertoolwarnung LNK4104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Export von Symbol 'Symbol' muss als PRIVATE angegeben sein  
  
 Als *Symbol* kommen folgende Funktionen in Frage:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllGetDocumentation`  
  
-   `DllInitialize`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllRegisterServerExW`  
  
-   `DllUnload`  
  
-   `DllUnregisterServer`  
  
-   `RasCustomDeleteEntryNotify`  
  
-   `RasCustomDial`  
  
-   `RasCustomDialDlg`  
  
-   `RasCustomEntryDlg`  
  
 Diese Warnung wird ausgegeben, wenn Sie eine Importbibliothek für eine DLL erstellen und eine der oben aufgeführten Funktionen exportieren, ohne sie in der Moduldefinitionsdatei als **PRIVATE** festzulegen.  Im Allgemeinen werden diese Funktionen nur für die Verwendung durch OLE exportiert.  Das Ablegen in der Importbibliothek kann zu ungewöhnlichem Verhalten führen, wenn die Funktionen unzulässigerweise von einem Programm aufgerufen werden, das mit dieser Bibliothek verknüpft ist.  Weitere Informationen über das **PRIVATE**\-Schlüsselwort finden Sie unter [EXPORTS](../../build/reference/exports.md).