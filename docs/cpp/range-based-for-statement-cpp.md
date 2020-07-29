---
title: Bereichsbasiert für Anweisung (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 1197080e2e96e0e5c51bc06e93026567a33c7842
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223615"
---
# <a name="range-based-for-statement-c"></a>Bereichsbasiert für Anweisung (C++)

Führt `statement` für jedes Element in `expression` wiederholt und nacheinander aus.

## <a name="syntax"></a>Syntax

> **`for (`***for-Range-Declaration* **`:`** *Ausdruck***`)`**\
&emsp;*Anweisung*

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die Bereichs basierte- **`for`** Anweisung zum Erstellen von Schleifen, die durch einen *Bereich*ausgeführt werden müssen, der als alles definiert ist, das Sie durchlaufen können – z. b. `std::vector` , oder eine beliebige andere C++-Standard Bibliotheks Sequenz, deren Bereich durch und definiert ist `begin()` `end()` . Der im-Teil deklarierte Name `for-range-declaration` ist für die **`for`** -Anweisung lokal und kann in oder nicht erneut deklariert `expression` werden `statement` . Beachten Sie, dass das- [`auto`](../cpp/auto-cpp.md) Schlüsselwort im-Teil der-Anweisung bevorzugt wird `for-range-declaration` .

**Neu in Visual Studio 2017:**  Bereichs basierte **`for`** Schleifen erfordern nicht mehr, dass `begin()` und `end()` Objekte desselben Typs zurückgeben. Dadurch kann `end()` ein sentinelobjekt zurückgegeben werden, z. b. verwendet von Bereichen, wie im Bereich "Bereiche-V3" definiert. Weitere Informationen finden Sie unter [generalisieren der Bereichs basierten `For` Schleife](https://wg21.link/p0184r0) und der [Range-V3-Bibliothek auf GitHub](https://github.com/ericniebler/range-v3).

In diesem Code wird gezeigt, wie Bereichs basierte **`for`** Schleifen verwendet werden, um ein Array und einen Vektor zu durchlaufen:

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

Eine Bereichs basierte **`for`** Schleife wird beendet, wenn eine dieser in `statement` ausgeführt wird: ein [`break`](../cpp/break-statement-cpp.md) , [`return`](../cpp/return-statement-cpp.md) oder [`goto`](../cpp/goto-statement-cpp.md) eine Anweisung mit einer Bezeichnung außerhalb der Bereichs basierten **`for`** Schleife. Eine- [`continue`](../cpp/continue-statement-cpp.md) Anweisung in einer Bereichs basierten **`for`** Schleife beendet nur die aktuelle Iterations-.

Beachten Sie diese Fakten zu Bereichs basiert **`for`** :

- Erkennt Arrays automatisch.

- Erkennt Container, die über `.begin()` und `.end()` verfügen.

- Verwendet die argumentabhängigen Suche `begin()` und `end()` für alles andere.

## <a name="see-also"></a>Siehe auch

[`auto`](../cpp/auto-cpp.md)<br/>
[Iterationsanweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[`while`-Anweisung (C++)](../cpp/while-statement-cpp.md)<br/>
[`do-while`-Anweisung (C++)](../cpp/do-while-statement-cpp.md)<br/>
[`for`-Anweisung (C++)](../cpp/for-statement-cpp.md)
