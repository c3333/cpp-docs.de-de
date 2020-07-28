---
title: Zugreifen auf C- oder C++-Daten in __asm-Blöcken
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: 8fbe855c2f5de96d81e6c8a27c4bfcee0864f12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193041"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>Zugreifen auf C- oder C++-Daten in __asm-Blöcken

**Microsoft-spezifisch**

Eine gute Möglichkeit der Inlineassembly ist die Möglichkeit, auf C-oder C++-Variablen anhand des Namens zu verweisen. Ein- **`__asm`** Block kann auf beliebige Symbole, einschließlich Variablennamen, verweisen, die sich im Bereich befinden, in dem der-Block angezeigt wird. Wenn sich z. b. die C-Variable im Gültigkeits `var` Bereich befindet, wird die Anweisung

```cpp
__asm mov eax, var
```

speichert den Wert von `var` in eax.

Wenn ein Klassen-, Struktur-oder Union-Member einen eindeutigen Namen hat, kann ein- **`__asm`** Block nur mit dem Elementnamen darauf verweisen, ohne die Variable oder den **`typedef`** Namen vor dem period-Operator (**.**) anzugeben. Wenn der Elementname jedoch nicht eindeutig ist, müssen Sie eine Variable oder einen **`typedef`** Namen direkt vor dem period-Operator platzieren. Beispielsweise werden die Strukturtypen in der folgenden Beispiel Freigabe `same_name` als Elementname angezeigt:.

Wenn Sie Variablen mit den Typen deklarieren

```cpp
struct first_type hal;
struct second_type oat;
```

alle Verweise auf den Member `same_name` müssen den Variablennamen verwenden, da `same_name` nicht eindeutig ist. Der Member `weasel` hat jedoch einen eindeutigen Namen, sodass Sie ihn nur mit seinem Elementnamen verweisen können:

```cpp
// InlineAssembler_Accessing_C_asm_Blocks.cpp
// processor: x86
#include <stdio.h>
struct first_type
{
   char *weasel;
   int same_name;
};

struct second_type
{
   int wonton;
   long same_name;
};

int main()
{
   struct first_type hal;
   struct second_type oat;

   __asm
   {
      lea ebx, hal
      mov ecx, [ebx]hal.same_name ; Must use 'hal'
      mov esi, [ebx].weasel       ; Can omit 'hal'
   }
   return 0;
}
```

Beachten Sie, dass das Weglassen des Variablen namens lediglich ein Codierungsaufwand ist. Die gleichen Assemblyanweisungen werden unabhängig davon generiert, ob der Variablenname vorhanden ist.

Sie können in C++ auf Datenelemente zugreifen, ohne die Zugriffsbeschränkungen zu berücksichtigen. Es ist jedoch nicht möglich, Element Funktionen aufzurufen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden von C oder C++ in __asm Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
