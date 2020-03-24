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
ms.openlocfilehash: cb340554bc20516175400c4d14a5d0dba934a313
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188960"
---
# <a name="__restrict"></a>__restrict

Wie der **__declspec ( [Einschränkungs](../cpp/restrict.md)**  -Modifizierer) gibt das **__restrict** -Schlüsselwort an, dass ein Symbol im aktuellen Gültigkeitsbereich nicht mit einem Alias versehen ist. Das **__restrict** -Schlüsselwort unterscheidet sich wie folgt vom `__declspec ( restrict )`-Modifizierer:

- Das **__restrict** -Schlüsselwort ist nur für-Variablen gültig, und `__declspec ( restrict )` ist nur für Funktions Deklarationen und-Definitionen gültig.

- **__restrict** ähnelt der Verwendung der C99- **Spezifikation, aber** **__restrict** können in C++ -oder-C-Programmen verwendet werden.

- Wenn **__restrict** verwendet wird, gibt der Compiler die No-Alias-Eigenschaft einer Variablen nicht weiter. Das heißt, wenn Sie einer Variablen, die nicht **__restrict** ist, eine **__restrict** Variable zuweisen, lässt der Compiler weiterhin zu, dass die nicht-__restrict Variable als Alias verwendet wird. Dies unterscheidet sich vom Verhalten des **Einschränkungs** Schlüsselworts aus der C99-Spezifikation.

Wenn Sie das Verhalten einer vollständigen Funktion beeinflussen, ist es im Allgemeinen besser, `__declspec ( restrict )` anstatt das Schlüsselwort zu verwenden.

Aus Gründen der Kompatibilität mit früheren Versionen ist **_Restrict** ein Synonym für **__restrict** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

In Visual Studio 2015 und höher können **__restrict** für C++ Verweise verwendet werden.

> [!NOTE]
>  Bei Verwendung in einer Variablen, die auch das [volatile](../cpp/volatile-cpp.md) -Schlüsselwort aufweist, hat **volatile** Vorrang.

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

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)
