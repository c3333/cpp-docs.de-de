---
title: Compilerwarnung (Stufe 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185203"
---
# <a name="compiler-warning-level-4-c4840"></a>Compilerwarnung (Stufe 4) C4840

> nicht Portier Bare Verwendung der '*Type*'-Klasse als Argument für eine Variadic-Funktion

## <a name="remarks"></a>Bemerkungen

Klassen oder Strukturen, die an eine Variadic-Funktion übermittelt werden, müssen trivial kopiert werden können. Wenn solche Objekte übergeben werden, macht der Compiler einfach eine bitweise Kopie und ruft keinen Konstruktor oder Destruktor auf.

Diese Warnung ist ab Visual Studio 2017 verfügbar.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4840 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

Für Zeichen folgen, die mit `CStringW`erstellt und verwaltet werden, sollte die angegebene `operator LPCWSTR()` verwendet werden, um ein `CStringW` Objekt in den Zeichen folgen Zeiger im C-Stil umzuwandeln, der von der Format Zeichenfolge erwartet wird

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
