---
title: Debug Iterator Support
ms.date: 09/13/2018
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
ms.openlocfilehash: a5773add9a26d647df6678ffa4f2681b73cff44f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231584"
---
# <a name="debug-iterator-support"></a>Debug Iterator Support

Mit der Laufzeitbibliothek von Visual C++ wird eine nicht ordnungsgemäße Verwendung eines Iterators erkannt, zur Laufzeit eine Assertanweisung ausgeführt und ein entsprechendes Dialogfeld angezeigt. Wenn Sie die Unterstützung für das Iteratordebugging aktivieren möchten, kompilieren Sie Ihr Programm mit Debugversionen der C++-Standardbibliothek und der C-Laufzeitbibliothek. Weitere Informationen finden Sie unter [CRT Library Features (CRT-Bibliotheksfunktionen)](../c-runtime-library/crt-library-features.md). Informationen zur Verwendung von überprüften Iteratoren finden Sie unter [Checked Iterators (Überprüfte Iteratoren)](../standard-library/checked-iterators.md).

In der C++-Standardbibliothek wird beschrieben, auf welche Weise Memberfunktionen dazu führen können, dass Iteratoren für einen Container ungültig werden. Zwei Beispiele:

- Durch das Löschen eines Elements in einem Container werden Iteratoren für das Element ungültig.

- Durch das Vergrößern eines [vector](../standard-library/vector.md)-Containers mittels „push“ oder „insert“ werden Iteratoren im `vector`-Container ungültig.

## <a name="invalid-iterators"></a>Ungültige Iteratoren

Wird dieses Beispielprogramm im Debugmodus kompiliert, wird eine Assertanweisung ausgeführt und das Programm wird beendet.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v {10, 15, 20};
   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="using-_iterator_debug_level"></a>Verwenden von _ITERATOR_DEBUG_LEVEL

Mit dem Präprozessormakro [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) können Sie die Funktion für das Iteratordebugging in einem Debugbuild deaktivieren. Von diesem Programm werden keine Assertanweisungen ausgeführt. Dennoch zeigt sich ein undefiniertes Verhalten.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v {10, 15, 20};

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="unitialized-iterators"></a>Unitialisierte Iteratoren

Eine Assertanweisung wird auch dann ausgeführt, wenn ein Iterator, wie im Folgenden dargestellt, vor der Initialisierung verwendet wird:

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="incompatible-iterators"></a>Inkompatible Iteratoren

Durch das folgende Codebeispiel wird eine Assertion verursacht, da die beiden Iteratoren für den [for_each](../standard-library/algorithm-functions.md#for_each)-Algorithmus nicht kompatibel sind. Für Algorithmen wird überprüft, ob von den bereitgestellten Iteratoren auf denselben Container verwiesen wird.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 {10, 20};
    vector<int> v2 {10, 20};

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

In diesem Beispiel wird anstelle eines functor-Objekts der Lambdaausdruck `[] (int& elem) { elem *= 2; }` verwendet. Dies hat zwar keinen Einfluss auf den Assertionsfehler (ein ähnliches functor-Objekt würde denselben Fehler verursachen). Dennoch eignen sich Lambdaausdrücke besonders gut für komplexe Funktionsobjektaufgaben. Weitere Informationen zu Lambda-Ausdrücken finden Sie unter [Lambda-Ausdrücke](../cpp/lambda-expressions-in-cpp.md).

## <a name="iterators-going-out-of-scope"></a>Iteratoren, die den Gültigkeitsbereich verlassen

Die Debug-iteratorüberprüfungen bewirken auch, dass eine Iteratorvariable, die in einer Schleife deklariert ist, **`for`** außerhalb des gültigen Bereichs liegt, wenn der **`for`** Schleifen Bereich endet.

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v {10, 15, 20};

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="destructors-for-debug-iterators"></a>Debugtoren für Debug-Iteratoren

Debugiteratoren enthalten nicht triviale Destruktoren. Wenn ein Dekonstruktor nicht ausgeführt wird, aber der Arbeitsspeicher des Objekts freigegeben wird, können Zugriffs Verletzungen und Daten Beschädigungen auftreten. Betrachten Sie dieses Beispiel:

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

int main() {
   std::vector<int> vect( 10 );
   base * pb = new derived( vect.begin() );
   delete pb;  // doesn't call ~derived()
   // access violation
}
```

## <a name="see-also"></a>Weitere Informationen

[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)
