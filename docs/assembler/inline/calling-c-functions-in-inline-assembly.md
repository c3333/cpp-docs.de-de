---
title: Aufrufen von C-Funktionen in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 94bbfda3a5fd15885f3d8276d506541418a9489f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169590"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Aufrufen von C-Funktionen in der Inlineassembly

**Microsoft-spezifisch**

Ein `__asm`-Block kann c-Funktionen, einschließlich c-Bibliotheks Routinen, aufruft. Im folgenden Beispiel wird die `printf` Bibliotheks Routine aufgerufen:

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

Da Funktionsargumente auf dem Stapel weitergegeben werden, übertragen Sie einfach die erforderlichen Argumente – Zeichen folgen Zeiger im vorherigen Beispiel –, bevor Sie die Funktion aufrufen. Die Argumente werden in umgekehrter Reihenfolge abgelegt, sodass Sie in der gewünschten Reihenfolge aus dem Stapel entfernt werden. So emulieren Sie die C-Anweisung

```cpp
printf( format, hello, world );
```

Das Beispiel überträgt Zeiger auf `world`, `hello`und `format`in dieser Reihenfolge und ruft dann `printf`auf.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
