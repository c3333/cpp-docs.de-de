---
title: Schreiben von Funktionen mit der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 5416a29477651c496d83e6ee215a2cb88ba26e3b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169057"
---
# <a name="writing-functions-with-inline-assembly"></a>Schreiben von Funktionen mit der Inlineassembly

**Microsoft-spezifisch**

Wenn Sie eine Funktion mit Inline-Assemblycode schreiben, ist es einfach, Argumente an die Funktion zu übergeben und einen Wert aus der Funktion zurückzugeben. Die folgenden Beispiele vergleichen eine Funktion, die zuerst für einen separaten Assembler geschrieben und anschließend für den Inline Assembler umgeschrieben wurde. Die Funktion, die als `power2`bezeichnet wird, empfängt zwei Parameter und multipliziert den ersten Parameter um 2 mit der Potenz des zweiten Parameters. Die-Funktion wird für einen separaten Assembler geschrieben und könnte wie folgt aussehen:

```asm
; POWER.ASM
; Compute the power of an integer
;
       PUBLIC _power2
_TEXT SEGMENT WORD PUBLIC 'CODE'
_power2 PROC

        push ebp        ; Save EBP
        mov ebp, esp    ; Move ESP into EBP so we can refer
                        ;   to arguments on the stack
        mov eax, [ebp+4] ; Get first argument
        mov ecx, [ebp+6] ; Get second argument
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )
        pop ebp         ; Restore EBP
        ret             ; Return with sum in EAX

_power2 ENDP
_TEXT   ENDS
        END
```

Da es für einen separaten Assembler geschrieben ist, erfordert die Funktion eine separate Quelldatei und Assembly und Verknüpfungs Schritte. C- C++ und Funktionsargumente werden in der Regel an den Stapel weitergegeben, sodass diese Version der `power2`-Funktion über ihre Positionen im Stapel auf ihre Argumente zugreift. (Beachten Sie, dass die **Model** -Direktive, die in MASM und einigen anderen Assemblern verfügbar ist, auch über den Namen auf Stapel Argumente und lokale Stapel Variablen zugreifen kann.)

## <a name="example"></a>Beispiel

Dieses Programm schreibt die `power2`-Funktion mit Inline-Assemblycode:

```cpp
// Power2_inline_asm.c
// compile with: /EHsc
// processor: x86

#include <stdio.h>

int power2( int num, int power );

int main( void )
{
    printf_s( "3 times 2 to the power of 5 is %d\n", \
              power2( 3, 5) );
}
int power2( int num, int power )
{
   __asm
   {
      mov eax, num    ; Get first argument
      mov ecx, power  ; Get second argument
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )
   }
   // Return with result in EAX
}
```

Die Inline Version der `power2`-Funktion verweist auf ihre Argumente anhand ihres Namens und wird in derselben Quelldatei wie der Rest des Programms angezeigt. Diese Version erfordert auch weniger Assemblyanweisungen.

Da die Inline Version von `power2` keine C `return`-Anweisung ausführt, wird eine harmlose Warnung ausgelöst, wenn Sie die Kompilierung mit der Warnstufe 2 oder höher durchführen. Die Funktion gibt einen Wert zurück, aber der Compiler kann dies nicht erkennen, wenn eine `return` Anweisung fehlt. Sie können [#pragma Warnung](../../preprocessor/warning.md) verwenden, um die Generierung dieser Warnung zu deaktivieren.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C oder C++ in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
