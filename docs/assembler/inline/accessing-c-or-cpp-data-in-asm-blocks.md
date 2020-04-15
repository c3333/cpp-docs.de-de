---
title: Zugreifen auf C- oder C++-Daten in __asm-Blöcken
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: b4341f87226118906749dcdb18b9227e68be6a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318088"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>Zugreifen auf C- oder C++-Daten in __asm-Blöcken

**Microsoft Specific**

Eine große Bequemlichkeit der Inline-Assembly ist die Möglichkeit, auf C- oder C++-Variablen nach Namen zu verweisen. Ein `__asm` Block kann auf alle Symbole verweisen, einschließlich Variablennamen, die sich im Bereich befinden, in dem der Block angezeigt wird. Wenn z. B. `var` die Variable C im Gültigkeitsbereich ist, wird die Anweisung

```cpp
__asm mov eax, var
```

speichert den `var` Wert von in EAX.

Wenn eine Klasse, Struktur oder ein Union-Member einen eindeutigen Namen hat, kann ein `__asm` Block `typedef` nur mit dem Membernamen darauf verweisen, ohne die Variable oder den Namen vor dem Periodenoperator (**.**) anzugeben. Wenn der Membername jedoch nicht eindeutig ist, `typedef` müssen Sie eine Variable oder einen Namen unmittelbar vor dem Periodenoperator platzieren. Beispielsweise geben die Strukturtypen im `same_name` folgenden Beispiel die Freigabe als Membername:.

Wenn Sie Variablen mit den Typen deklarieren

```cpp
struct first_type hal;
struct second_type oat;
```

Alle Verweise auf `same_name` den Member müssen `same_name` den Variablennamen verwenden, da er nicht eindeutig ist. Das Mitglied `weasel` hat jedoch einen eindeutigen Namen, sodass Sie nur mit seinem Mitgliedsnamen darauf verweisen können:

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

Beachten Sie, dass das Weglassen des Variablennamens lediglich eine Codierungs-Komfort ist. Es werden dieselben Assemblyanweisungen generiert, unabhängig davon, ob der Variablenname vorhanden ist oder nicht.

Sie können ohne Rücksicht auf Zugriffsbeschränkungen auf Datenmember in C++ zugreifen. Sie können jedoch keine Memberfunktionen aufrufen.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden von C oder C++ in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
