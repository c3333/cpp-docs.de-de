---
title: Bereichsbasiert für Anweisung (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 504f177cf68b978642f15ba4799cab8cb517f447
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188349"
---
# <a name="range-based-for-statement-c"></a>Bereichsbasiert für Anweisung (C++)

Führt `statement` für jedes Element in `expression` wiederholt und nacheinander aus.

## <a name="syntax"></a>Syntax

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Bemerkungen

Mithilfe der Bereichs basierten **for** -Anweisung können Sie Schleifen erstellen, die durch einen "Bereich" ausgeführt werden müssen, der als alles definiert ist, das Sie durchlaufen können – z. b. `std::vector`C++ oder eine beliebige andere Standard Bibliotheks Sequenz, deren Bereich durch eine `begin()` und `end()`definiert ist. Der im `for-range-declaration` Teil deklarierte Name ist für die **for** -Anweisung lokal und kann in `expression` oder `statement`nicht erneut deklariert werden. Beachten Sie, dass das Schlüsselwort " [Auto](../cpp/auto-cpp.md) " im `for-range-declaration` Teil der Anweisung bevorzugt wird.

**Neu in Visual Studio 2017:**  Bereichs basierte for-Schleifen erfordern nicht mehr, dass Begin () und End () Objekte desselben Typs zurückgeben. Dadurch kann end() ein Sentinelobjekt zurückgeben, das von Bereichen verwendet wird, die im Ranges-V3-Vorschlag definiert sind. Weitere Informationen finden Sie unter [Generalizing the Range-Based For Loop (Bereichsbasierte for-Schleife generalisieren)](https://wg21.link/p0184r0) und [range-v3 library on GitHub (Range-v3-Bibliothek auf GitHub)](https://github.com/ericniebler/range-v3).

Dieser Code zeigt, wie Sie Bereichs basierte **for** -Schleifen verwenden, um ein Array und einen Vektor zu durchlaufen:

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

Hier sehen Sie die Ausgabe:

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

Eine Bereichs basierte **for** -Schleife wird beendet, wenn eine dieser [Vorgänge](../cpp/goto-statement-cpp.md) in `statement` ausgeführt wird: eine unter [Brechung](../cpp/break-statement-cpp.md), eine [Rückgabe](../cpp/return-statement-cpp.md)oder eine gehe zu einer Anweisung, die außerhalb der Bereichs basierten **for** -Schleife liegt. Eine [Continue](../cpp/continue-statement-cpp.md) -Anweisung in einer Bereichs basierten **for** -Schleife beendet nur die aktuelle Iterations Anweisung.

Beachten Sie diese Fakten zu Bereichs basiert **für**:

- Erkennt Arrays automatisch.

- Erkennt Container, die über `.begin()` und `.end()` verfügen.

- Verwendet die argumentabhängigen Suche `begin()` und `end()` für alles andere.

## <a name="see-also"></a>Weitere Informationen

[auto](../cpp/auto-cpp.md)<br/>
[Iterationsanweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[while-Anweisung (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while-Anweisung (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for-Anweisung (C++)](../cpp/for-statement-cpp.md)
