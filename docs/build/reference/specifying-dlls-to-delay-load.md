---
title: "Festlegen von DLLs, um das verzögerte Laden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bfa7eb3c862c1ce5d1ed356ddd89c51ebff95860
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-dlls-to-delay-load"></a>Festlegen von DLLs für verzögertes Laden
Sie können angeben, welche die DLLs für verzögertes Laden, mit der [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md):`dllname` (Linkeroption). Wenn Sie nicht beabsichtigen, Ihre eigene Version einer Hilfsfunktion zu verwenden, müssen Sie auch das Programm mit "delayimp.lib" (für Desktopanwendungen) oder "dloadhelper.lib" (für Store-Apps) verknüpfen.  
  
 Im Folgenden finden Sie ein einfaches Beispiel für das verzögerte Laden einer DLL:  
  
```  
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll  
#include <windows.h>  
// uncomment these lines to remove .libs from command line  
// #pragma comment(lib, "delayimp")  
// #pragma comment(lib, "user32")  
  
int main() {  
   // user32.dll will load at this point  
   MessageBox(NULL, "Hello", "Hello", MB_OK);  
}  
```  
  
 Erstellen Sie die Debugversion des Projekts. Durchlaufen Sie den Code mithilfe des Debuggers schrittweise; Sie werden bemerken, dass "user32.dll" nur geladen wird, wenn Sie `MessageBox` aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Linkerunterstützung für verzögertes Laden von DLLs](../../build/reference/linker-support-for-delay-loaded-dlls.md)