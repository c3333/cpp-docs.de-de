---
title: Checked Iterators
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: 2327638208f30908cd3429ae656ce569f5821195
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684902"
---
# <a name="checked-iterators"></a>Checked Iterators

Aktivierte Iteratoren stellen sicher, dass die Grenzen des Containers nicht überschrieben werden. Überprüfte Iteratoren werden auf Releasebuilds und auf Debugbuilds angewendet. Weitere Informationen zur Verwendung von Debugiteratoren beim Kompilieren im Debugmodus finden Sie unter [Debug Iterator Support (Unterstützung für Iteratordebugging)](../standard-library/debug-iterator-support.md).

## <a name="remarks"></a>Bemerkungen

Informationen über das Deaktivieren der Warnungen, die für überprüfte Iteratoren generiert werden, finden Sie unter [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

Sie können das Präprozessormakro [ \_ \_ iteratordebuggen \_ ](../standard-library/iterator-debug-level.md) verwenden, um die Funktion für aktivierte Iteratoren zu aktivieren bzw. zu deaktivieren. Wenn _ITERATOR_DEBUG_LEVEL als 1 oder 2 definiert ist, verursacht die unsichere Verwendung von Iteratoren einen Laufzeitfehler und das Programm wird beendet. Lautet die Definition 0, werden aktivierte Iteratoren deaktiviert. Standardmäßig ist der Wert für _ITERATOR_DEBUG_LEVEL 0 für Releasebuilds und 2 für Debugbuilds.

> [!IMPORTANT]
> Ältere Dokumentationen und Quellcode beziehen sich möglicherweise auf das [_SECURE_SCL](../standard-library/secure-scl.md)-Makro. Verwenden Sie _ITERATOR_DEBUG_LEVEL, um _SECURE_SCL zu steuern. Weitere Informationen finden Sie unter [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

Wenn _ITERATOR_DEBUG_LEVEL als 1 oder 2 definiert ist, werden diese iteratorüberprüfungen ausgeführt:

- Alle Standarditeratoren (beispielsweise [vector::iterator](../standard-library/vector-class.md#iterator)) werden überprüft.

- Wenn ein Ausgabeiterator ein überprüfter Iterator ist, wird das Verhalten von Aufrufen der Standardbibliotheksfunktionen wie [std::copy](../standard-library/algorithm-functions.md#copy) überprüft.

- Wenn ein Ausgabeiterator ein nicht überprüfter Iterator ist, verursachen Aufrufe der Standardbibliotheksfunktionen Compilerwarnungen.

- Die folgenden Funktionen verursachen einen Laufzeitfehler, wenn ein Zugriff außerhalb der Grenzen des Containers erfolgt:

:::row:::
   :::column span="":::
      &emsp;&emsp;[`basic_string::operator[]`](../standard-library/basic-string-class.md#op_at)\
      &emsp;&emsp;[`bitset::operator[]`](../standard-library/bitset-class.md#op_at)\
      &emsp;&emsp;[`deque::back`](../standard-library/deque-class.md#back)\
      &emsp;&emsp;[`deque::front`](../standard-library/deque-class.md#front)
   :::column-end:::
   :::column span="":::
      [`deque::operator[]`](../standard-library/deque-class.md#op_at)\
      [`list::back`](../standard-library/list-class.md#back)\
      [`list::front`](../standard-library/list-class.md#front)\
      [`queue::back`](../standard-library/queue-class.md#back)
   :::column-end:::
   :::column span="":::
      [`queue::front`](../standard-library/queue-class.md#front)\
      [`vector::back`](../standard-library/vector-class.md#back)\
      [`vector::front`](../standard-library/vector-class.md#front)\
      [`vector::operator[]`](../standard-library/vector-class.md#op_at)
   :::column-end:::
:::row-end:::

Wenn _ITERATOR_DEBUG_LEVEL als 0 definiert ist:

- Alle Standarditeratoren werden nicht überprüft. Iteratoren können über die Containergrenzen hinausgehen, was zu nicht definiertem Verhalten führt.

- Wenn ein Ausgabeiterator ein überprüfter Iterator ist, wird das Verhalten von Aufrufen der Standardbibliotheksfunktionen wie `std::copy` überprüft.

- Wenn ein Ausgabeiterator ein nicht überprüfter Iterator ist, wird das Verhalten von Aufrufen der Standardbibliotheksfunktionen nicht überprüft.

Ein überprüfter Iterator bezieht sich auf einen Iterator, der `invalid_parameter_handler` aufruft, wenn Sie versuchen, über die Grenzen des Containers hinauszuwechseln. Weitere Informationen über `invalid_parameter_handler` finden Sie unter [Parametervalidierung](../c-runtime-library/parameter-validation.md).

Die Iteratoradaptoren, die überprüfte Iteratoren unterstützen, sind die [checked_array_iterator-Klasse](../standard-library/checked-array-iterator-class.md) und die [unchecked_array_iterator-Klasse](../standard-library/unchecked-array-iterator-class.md).

## <a name="examples"></a>Beispiele

Wenn Sie mit _ITERATOR_DEBUG_LEVEL auf 1 oder 2 festgelegt haben, tritt ein Laufzeitfehler auf, wenn Sie versuchen, auf ein Element zuzugreifen, das sich außerhalb der Grenzen des Containers befindet, indem Sie den Indizierungs Operator bestimmter Klassen verwenden.

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

Dieses Programm gibt „67“ aus und zeigt dann ein Assertionsfehlerdialogfeld mit zusätzlichen Informationen zu dem Fehler an.

Wenn Sie die Kompilierung mit _ITERATOR_DEBUG_LEVEL auf 1 oder 2 festlegen, tritt ein Laufzeitfehler auf, wenn Sie versuchen, mithilfe von oder in Containerklassen auf ein Element zuzugreifen, `front` `back` Wenn der Container leer ist.

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

Dieses Programm zeigt ein Assertionsfehlerdialogfeld mit zusätzlichen Informationen zu dem Fehler an.

Im folgenden Code werden verschiedene Anwendungsfälle für Iteratoren mit Kommentaren veranschaulicht. Standardmäßig ist _ITERATOR_DEBUG_LEVEL in Debugbuilds auf 2 und in Einzelhandels Builds auf 0 (null) festgelegt.

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Beim Kompilieren dieses Codes mit `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` gibt der Compiler eine Warnung aus, die Kompilierung erfolgt aber ohne Fehler in eine ausführbare Datei:

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

Bei der Ausführung in der Befehlszeile erzeugt die ausführbare Datei die folgende Ausgabe:

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>Weitere Informationen

[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)\
[Iteratorunterstützung Debuggen](../standard-library/debug-iterator-support.md)
