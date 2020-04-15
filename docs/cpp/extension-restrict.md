---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360817"
---
# <a name="__restrict"></a>__restrict

Wie der Modifikator **__declspec ( [einschränken](../cpp/restrict.md) )** gibt das **Schlüsselwort __restrict** an, dass ein Symbol im aktuellen Bereich nicht aliasiert wird. Das **Schlüsselwort __restrict** `__declspec ( restrict )` unterscheidet sich wie folgt vom Modifikator:

- Das **Schlüsselwort __restrict** ist nur `__declspec ( restrict )` für Variablen gültig und nur für Funktionsdeklarationen und Definitionen gültig.

- **__restrict** ist ähnlich wie die C99-Spezifikation **einschränken,** aber **__restrict** können in C++- oder C-Programmen verwendet werden.

- Wenn **__restrict** verwendet wird, gibt der Compiler die no-alias-Eigenschaft einer Variablen nicht aus. Das heißt, wenn Sie einer nicht **__restrict** Variablen eine **__restrict** zuweisen, lässt der Compiler weiterhin zu, dass die nicht __restrict Variable aliasiert wird. Dies unterscheidet sich vom Verhalten des **Schlüsselworts restrict** aus der C99-Spezifikation.

Wenn Sie das Verhalten einer vollständigen Funktion beeinflussen, ist es im Allgemeinen besser, `__declspec ( restrict )` anstatt das Schlüsselwort zu verwenden.

Aus Kompatibilität mit früheren Versionen ist **_restrict** ein Synonym für **__restrict** es sei denn, die Compileroption [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) wird angegeben.

In Visual Studio 2015 und höher können **__restrict** für C++-Referenzen verwendet werden.

> [!NOTE]
> Bei Verwendung für eine Variable, die auch das [volatile](../cpp/volatile-cpp.md) Schlüsselwort hat, hat **volatile** Vorrang.

## <a name="example"></a>Beispiel

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)
