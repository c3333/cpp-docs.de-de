---
title: Bereinigen von Ressourcen
description: Freigeben von Ressourcen während eines Beendigungs Handlers für die strukturierte Ausnahmebehandlung.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: dae92a515db25b9985a890d7d08cc213f88ecfea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898433"
---
# <a name="cleaning-up-resources"></a>Bereinigen von Ressourcen

Während der Beendigung der handlerausführung wissen Sie möglicherweise nicht, welche Ressourcen abgerufen wurden, bevor der Beendigungs Handler aufgerufen wurde. Es ist möglich, dass der **`__try`** Anweisungsblock unterbrochen wurde, bevor alle Ressourcen abgerufen wurden, sodass nicht alle Ressourcen geöffnet wurden.

Um sicher zu sein, sollten Sie überprüfen, welche Ressourcen geöffnet sind, bevor Sie mit der Bereinigung der Beendigungs Behandlung fortfahren. Dazu wird diese Vorgehensweise empfohlen:

1. Initialisieren Sie die Handles mit dem Wert NULL.

1. Rufen Sie im **`__try`** Anweisungsblock Ressourcen ab. Handles werden auf positive Werte festgelegt, wenn die Ressource abgerufen wird.

1. Geben Sie im **`__finally`** Anweisungsblock jede Ressource frei, deren zugehörige handle-oder Flag-Variable ungleich 0 (null) oder nicht NULL ist.

## <a name="example"></a>Beispiel

Der folgende Code verwendet beispielsweise einen Beendigungs Handler, um drei Dateien zu schließen und einen Speicherblock freizugeben. Diese Ressourcen wurden im- **`__try`** Anweisungsblock abgerufen. Vor dem Bereinigen einer Ressource prüft der Code zunächst, ob die Ressource abgerufen wurde.

```cpp
// exceptions_Cleaning_up_Resources.cpp
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void fileOps() {
   FILE  *fp1 = NULL,
         *fp2 = NULL,
         *fp3 = NULL;
   LPVOID lpvoid = NULL;
   errno_t err;

   __try {
      lpvoid = malloc( BUFSIZ );

      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );
      err = fopen_s(&fp3, "CARS.DAT", "w+" );
   }
   __finally {
      if ( fp1 )
         fclose( fp1 );
      if ( fp2 )
         fclose( fp2 );
      if ( fp3 )
         fclose( fp3 );
      if ( lpvoid )
         free( lpvoid );
   }
}

int main() {
   fileOps();
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
