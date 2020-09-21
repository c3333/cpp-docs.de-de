---
title: Compilerfehler C2057
ms.date: 11/04/2016
f1_keywords:
- C2057
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
ms.openlocfilehash: bdcf97ab6ea877af4e0713fc96ffd38f299e8234
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741448"
---
# <a name="compiler-error-c2057"></a>Compilerfehler C2057

Konstanter Ausdruck erwartet

Der Kontext erfordert einen konstanten Ausdruck bzw. einen Ausdruck, dessen Wert zur Kompilierzeit bekannt ist.

Der Compiler muss die Größe eines Typs zur Kompilierungszeit kennen, um Speicherplatz für eine Instanz dieses Typs zuzuweisen.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2057 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

C# verfügt über restriktivere Regeln für konstante Ausdrücke.  Im folgenden Beispiel wird C2057 generiert und gezeigt, wie Sie diesen Fehler beheben:

```c
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```
