---
title: Compilerfehler C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: b95c6459c0ff093d22f3e754f2c7fd6564d2b296
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221197"
---
# <a name="compiler-error-c2361"></a>Compilerfehler C2361

die Initialisierung von "Identifier" wird von der Bezeichnung "Default" übersprungen.

Die Initialisierung von `identifier` kann in einer-Anweisung übersprungen werden **`switch`** . Sie können nur dann eine Deklaration mit einem Initialisierer überspringen, wenn die Deklaration in einen-Block eingeschlossen ist. (Sofern Sie nicht in einem-Block deklariert wird, befindet sich die-Variable bis zum Ende der-Anweisung im Gültigkeitsbereich **`switch`** .)

Im folgenden Beispiel wird C2361 generiert:

```cpp
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

Mögliche Lösung:

```cpp
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```
