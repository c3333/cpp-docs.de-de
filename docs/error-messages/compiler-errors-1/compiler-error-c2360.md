---
title: Compilerfehler C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: a2a164f919dc7535a4587d51f4f7dba8653a1760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214684"
---
# <a name="compiler-error-c2360"></a>Compilerfehler C2360

die Initialisierung von "Identifier" wird von der Case-Bezeichnung übersprungen.

Die Initialisierung von `identifier` kann in einer-Anweisung übersprungen werden **`switch`** . Sie können nur dann eine Deklaration mit einem Initialisierer überspringen, wenn die Deklaration in einen-Block eingeschlossen ist. (Sofern Sie nicht in einem-Block deklariert wird, befindet sich die-Variable bis zum Ende der-Anweisung im Gültigkeitsbereich **`switch`** .)

Im folgenden Beispiel wird C2360 generiert:

```cpp
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Mögliche Lösung:

```cpp
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```
