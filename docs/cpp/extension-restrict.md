---
title: '`__restrict`'
description: Beschreibt das Microsoft Visual C++- `__restrict` Schlüsselwort.
ms.date: 11/6/2020
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.openlocfilehash: f23574f49712928e0095f29a3b88b0c05b185eab
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381570"
---
# `__restrict`

Wie der-Modifizierer **`__declspec` ( [`restrict`](../cpp/restrict.md) )** gibt das- **`__restrict`** Schlüsselwort (zwei führende Unterstriche ' _ ') an, dass ein Symbol im aktuellen Gültigkeitsbereich nicht mit einem Alias versehen ist. Das- **`__restrict`** Schlüsselwort unterscheidet `__declspec (restrict)` sich wie folgt vom-Modifizierer:

- Das **`__restrict`** Schlüsselwort ist nur für Variablen gültig und `__declspec (restrict)` nur für Funktions Deklarationen und-Definitionen gültig.

- **`__restrict`** ähnelt [`restrict`](../c-language/type-qualifiers.md#restrict) für C ab C99, **`__restrict`** kann jedoch sowohl in C++-als auch in C-Programmen verwendet werden.

- Wenn **`__restrict`** verwendet wird, gibt der Compiler die No-Alias-Eigenschaft einer Variablen nicht weiter. Das heißt, wenn Sie einer **`__restrict`** nicht Variablen eine Variable zuweisen **`__restrict`** , lässt der Compiler weiterhin zu, dass für die nicht-__restrict Variable ein Alias verwendet wird. Dies unterscheidet sich vom Verhalten des C99-C-Programmiersprachen- **`restrict`** Schlüssel Worts.

Wenn Sie das Verhalten einer gesamten Funktion beeinflussen möchten, verwenden Sie im allgemeinen **`__declspec (restrict)`** anstelle des-Schlüssel Worts.

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_restrict`** ein Synonym für, **`__restrict`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

In Visual Studio 2015 und höher **`__restrict`** kann für C++-Verweise verwendet werden.

> [!NOTE]
> Wenn Sie für eine Variable verwendet wird, die auch das- [`volatile`](../cpp/volatile-cpp.md) Schlüsselwort aufweist, hat **`volatile`** Vorrang.

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
