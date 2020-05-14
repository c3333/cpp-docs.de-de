---
title: Überlegungen zum Schreiben von Prolog- und Epilogcode
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: e1559c75808a72cd3f9674399bec036cf392b44f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334579"
---
# <a name="considerations-when-writing-prologepilog-code"></a>Überlegungen zum Schreiben von Prolog- und Epilogcode

**Microsoft-spezifisch**

Vor dem Schreiben eigener Prolog- und Epilogcodesequenzen ist es wichtig, zu verstehen, wie der Stapelrahmen festgelegt ist. Es ist auch hilfreich zu wissen, wie die vordefinierte **__LOCAL_SIZE**-Konstante verwendet werden kann.

## <a name="cstack-frame-layout"></a><a name="_clang_c_stack_frame_layout"></a> C-Stapelrahmenlayout

In diesem Beispiel wird der Standardprologcode veranschaulicht, der in einer 32-Bit-Funktion enthalten sein kann:

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

Die `localbytes`-Variable gibt die Anzahl von Bytes an, die auf dem Stapel für lokale Variablen erforderlich sind. Die `registers`-Variable ist ein Platzhalter, der die Liste der Register darstellt, die auf dem Stapel gespeichert werden sollen. Nach dem Verschieben der Register können Sie alle weiteren entsprechenden Daten auf dem Stapel platzieren. Im Folgenden wird der entsprechende Epilogcode dargestellt:

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

Der Stapel wächst immer nach unten (von hohen zu niedrigen Speicheradressen). Der Basiszeiger (`ebp`) zeigt auf den abgelegten `ebp`-Wert. Der Gültigkeitsbereich der lokalen Variablen beginnt bei `ebp-2`. Um auf lokale Variablen zuzugreifen, berechnen Sie einen Offset von `ebp`, indem Sie den entsprechenden Wert von `ebp` subtrahieren.

## <a name="the-__local_size-constant"></a><a name="_clang_the___local_size_constant"></a> Die __LOCAL_SIZE-Konstante

Der Compiler stellt eine Konstante, **__LOCAL_SIZE**, für die Verwendung im Inlineassemblerblock des Funktionsprologcodes bereit. Mit dieser Konstanten wird Speicherplatz für lokale Variablen im Stapelrahmen im benutzerdefinierten Prologcode zugeordnet.

Der Compiler bestimmt den Wert von **__LOCAL_SIZE**. Der Wert ist die Gesamtzahl von Bytes aller benutzerdefinierten lokalen Variablen und der vom Compiler generierten temporären Variablen. **__LOCAL_SIZE** kann nur als unmittelbarer Operand verwendet werden. Er kann nicht in einem Ausdruck verwendet werden. Sie dürfen den Wert dieser Konstanten nicht ändern oder neu definieren. Zum Beispiel:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

Das folgende Beispiel einer bloßen Funktion, welche benutzerdefinierte Prolog- und Epilogsequenzen enthält, verwendet **__LOCAL_SIZE** in der Prologsequenz:

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Naked-Funktionen](../c-language/naked-functions.md)
