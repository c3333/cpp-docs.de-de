---
title: Regeln und Einschränkungen für Naked-Funktionen
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: 1eb2875514621e567701b6197d3ad6695457506b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178950"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Regeln und Einschränkungen für Naked-Funktionen

**Microsoft-spezifisch**

Die folgenden Regeln und Einschränkungen treffen auf naked-Funktionen zu:

- Die **Return** -Anweisung ist nicht zulässig.

- Konstrukte für die strukturierte Ausnahmebehandlung und C++-Ausnahmebehandlung sind nicht zulässig, da sie über den Stapelrahmen entladen werden müssen.

- Aus demselben Grund ist jede Form von `setjmp` nicht zulässig.

- Die Verwendung der `_alloca`-Funktion ist nicht zulässig.

- Um sicherzustellen, dass kein Initialisierungscode für lokale Variablen vor der Prologsequenz vorkommt, sind initialisierte lokale Variablen im Funktionsbereich nicht zulässig. Insbesondere ist die Deklaration von C++-Objekten im Funktionsbereich nicht zulässig. Es können jedoch initialisierte Daten in einem geschachtelten Bereich vorhanden sein.

- Framezeigeroptimierung (die Compileroption "/Oy") wird nicht empfohlen, sie wird jedoch für eine naked-Funktion automatisch unterdrückt.

- Sie können C++-Klassenobjekte nicht im lexikalischen Bereich der Funktion deklarieren. Sie können jedoch Objekte in einem geschachtelten Block deklarieren.

- Das **Naked** -Schlüsselwort wird beim Kompilieren mit [/CLR](../build/reference/clr-common-language-runtime-compilation.md)ignoriert.

- Wenn für [__fastcall](../cpp/fastcall.md) Naked-Funktionen ein Verweis in C/C++ Code auf eines der Register Argumente vorhanden ist, sollte der Prolog Code die Werte von speichern, die sich bei dem Stapel Speicherort für diese Variable registrieren. Beispiel:

```cpp
// nkdfastcl.cpp
// compile with: /c
// processor: x86
__declspec(naked) int __fastcall  power(int i, int j) {
   // calculates i^j, assumes that j >= 0

   // prolog
   __asm {
      push ebp
      mov ebp, esp
      sub esp, __LOCAL_SIZE
     // store ECX and EDX into stack locations allocated for i and j
     mov i, ecx
     mov j, edx
   }

   {
      int k = 1;   // return value
      while (j-- > 0)
         k *= i;
      __asm {
         mov eax, k
      };
   }

   // epilog
   __asm {
      mov esp, ebp
      pop ebp
      ret
   }
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Naked-Funktionsaufrufe](../cpp/naked-function-calls.md)
