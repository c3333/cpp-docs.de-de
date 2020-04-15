---
title: Überlegungen für das Schreiben des Prolog-/Epilogcodes
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: cda6a6c82efcf30a916aced121024095d7ce8138
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337111"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Überlegungen für das Schreiben des Prolog-/Epilogcodes

**Microsoft Specific**

Bevor Sie Ihre eigenen Prolog- und Epilog-Codesequenzen schreiben, ist es wichtig zu verstehen, wie der Stapelrahmen angeordnet ist. Es ist auch nützlich zu `__LOCAL_SIZE` wissen, wie man das Symbol verwendet.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Stack Frame Layout

In diesem Beispiel wird der Standardprologcode veranschaulicht, der in einer 32-Bit-Funktion enthalten sein kann:

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

Die `localbytes`-Variable gibt die Anzahl von Bytes an, die auf dem Stapel für lokale Variablen erforderlich sind. Die `<registers>`-Variable ist ein Platzhalter, der die Liste der Register darstellt, die auf dem Stapel gespeichert werden sollen. Nach dem Verschieben der Register können Sie alle weiteren entsprechenden Daten auf dem Stapel platzieren. Im Folgenden wird der entsprechende Epilogcode dargestellt:

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

Der Stapel wächst immer nach unten (von hohen zu niedrigen Speicheradressen). Der Basiszeiger (`ebp`) zeigt auf den abgelegten `ebp`-Wert. Der Gültigkeitsbereich der lokalen Variablen beginnt bei `ebp-4`. Um auf lokale Variablen zuzugreifen, berechnen Sie einen Offset von `ebp`, indem Sie den entsprechenden Wert von `ebp` subtrahieren.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a>__LOCAL_SIZE

Der Compiler stellt `__LOCAL_SIZE`ein Symbol bereit, , für die Verwendung im Inline-Assemblerblock des Funktionsprologcodes. Mit diesem Symbol wird Speicherplatz für lokale Variablen im Stapelrahmen im benutzerdefinierten Prologcode zugeordnet.

Der Compiler bestimmt `__LOCAL_SIZE`den Wert von . Sein Wert ist die Gesamtzahl von Bytes aller benutzerdefinierten lokalen Variablen und der vom Compiler generierten temporären Variablen. `__LOCAL_SIZE`kann nur als sofortiger Operand verwendet werden; Sie kann nicht in einem Ausdruck verwendet werden. Sie dürfen den Wert dieses Symbols nicht ändern oder neu definieren. Beispiel:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

Das folgende Beispiel einer nackten Funktion, die benutzerdefinierte `__LOCAL_SIZE` Prolog- und Epilogsequenzen enthält, verwendet das Symbol in der Prologsequenz:

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Naked-Funktionsaufrufe](../cpp/naked-function-calls.md)
