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
ms.openlocfilehash: 73be1142747dc608d683e6bd847639b9df718a13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192625"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Aufrufen von C-Funktionen in der Inlineassembly

**Microsoft-spezifisch**

Ein- **`__asm`** Block kann c-Funktionen, einschließlich c-Bibliotheks Routinen, aufruft. Im folgenden Beispiel wird die `printf` Bibliotheks Routine aufgerufen:

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

Das Beispiel überträgt Zeiger auf `world` , `hello` und `format` in dieser Reihenfolge und ruft dann auf `printf` .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
