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
ms.openlocfilehash: 6318e6d78f6c4c4bb6827a79d26bca028dfe3f3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233742"
---
# <a name="__restrict"></a>__restrict

Wie der **__declspec ( [Einschränkungs](../cpp/restrict.md) ** -Modifizierer) gibt das- **`__restrict`** Schlüsselwort an, dass ein Symbol im aktuellen Gültigkeitsbereich nicht mit einem Alias versehen ist. Das- **`__restrict`** Schlüsselwort unterscheidet `__declspec ( restrict )` sich wie folgt vom-Modifizierer:

- Das **`__restrict`** Schlüsselwort ist nur für Variablen gültig und `__declspec ( restrict )` nur für Funktions Deklarationen und-Definitionen gültig.

- **`__restrict`** ähnelt **`restrict`** von der C99-Spezifikation, kann aber **`__restrict`** in C++-oder C-Programmen verwendet werden.

- Wenn **`__restrict`** verwendet wird, gibt der Compiler die No-Alias-Eigenschaft einer Variablen nicht weiter. Das heißt, wenn Sie einer **`__restrict`** nicht Variablen eine Variable zuweisen **`__restrict`** , lässt der Compiler weiterhin zu, dass für die nicht-__restrict Variable ein Alias verwendet wird. Dies unterscheidet sich vom Verhalten des- **`restrict`** Schlüssel Worts aus der C99-Spezifikation.

Wenn Sie das Verhalten einer vollständigen Funktion beeinflussen, ist es im Allgemeinen besser, `__declspec ( restrict )` anstatt das Schlüsselwort zu verwenden.

Aus Gründen der Kompatibilität mit früheren Versionen ist **_Restrict** ein Synonym für, **`__restrict`** es sei denn, die Compileroption [/Za \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

In Visual Studio 2015 und höher **`__restrict`** kann für C++-Verweise verwendet werden.

> [!NOTE]
> Wenn Sie für eine Variable verwendet wird, die auch das [volatile](../cpp/volatile-cpp.md) -Schlüsselwort aufweist, hat **`volatile`** Vorrang.

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

[Schlüsselwörter](../cpp/keywords-cpp.md)
