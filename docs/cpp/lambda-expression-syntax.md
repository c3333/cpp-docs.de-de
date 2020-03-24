---
title: Lambdaausdruckssyntax
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 9ac2fdea1a8fc8dcf2b03059455c3141daf86aa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179652"
---
# <a name="lambda-expression-syntax"></a>Lambdaausdruckssyntax

Dieser Artikel beschreibt Syntax und Strukturelemente von Lambdaausdrücken. Eine Beschreibung der Lambda-Ausdrücke finden Sie unter [Lambda-Ausdrücke](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>Funktionsobjekte und Lambdas

Wenn Sie Code schreiben, verwenden Sie wahrscheinlich Funktionszeiger und Funktions Objekte, um Probleme zu lösen und Berechnungen auszuführen, insbesondere bei der Verwendung [ C++ von Standard Bibliotheks Algorithmen](../cpp/algorithms-modern-cpp.md). Funktionszeiger und Funktionsobjekte haben beide Vorteile und Nachteile – z. B. weisen Funktionszeiger minimalen syntaktischen Mehraufwand auf, behalten aber innerhalb eines Bereichs den Zustand nicht bei. Hingegen können Funktionsobjekte den Zustand zwar beibehalten, erfordern allerdings den syntaktischen Mehraufwand einer Klassendefinition.

Bei einem Lambda werden die Vorteile von Funktionszeigern und Funktionsobjekten kombiniert und deren Nachteile gleichzeitig vermieden. Wie bei Funktionsobjekten ist ein Lambda flexibel und kann den Zustand beibehalten, aber anders als ein Funktionsobjekt benötigt seine kompakte Syntax keine explizite Klassendefinition. Mit der Verwendung von Lambdas können Sie Code schreiben, der weniger schwerfällig und weniger fehleranfällig als Code für ein entsprechendes Funktionsobjekt ist.

In den folgenden Beispielen wird die Verwendung eines Lambda-Ausdrucks mit der Verwendung eines Funktionsobjekts verglichen. Im ersten Beispiel wird ein Lambda-Ausdruck verwendet, um auf der Konsole auszugeben, ob jedes Element in einem `vector`-Objekt gerade oder ungerade ist. Im zweiten Beispiel wird für die gleiche Aufgabe ein Funktionsobjekt verwendet.

## <a name="example-1-using-a-lambda"></a>Beispiel 1: Verwendung eines Lambda-Ausdrucks

In diesem Beispiel wird ein Lambda an die **for_each** -Funktion weitergeleitet. Lambda druckt ein Ergebnis, das besagt, ob jedes Element in einem `vector` -Objekt ist, gerade oder ungerade.

### <a name="code"></a>Code

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>Kommentare

Im Beispiel ist das dritte Argument für die **for_each** -Funktion eine Lambda-Funktion. Mit dem `[&evenCount]`-Teil wird die Erfassungsklausel des Ausdrucks angegeben. Mit `(int n)` wird die Parameterliste und mit dem Rest der Text des Ausdrucks angegeben.

## <a name="example-2-using-a-function-object"></a>Beispiel 2: Verwendung eines Funktionsobjekts

Manchmal wäre die Ausweitung eines Lambdas über den Umfang des vorherigen Beispiels hinaus zu hinderlich. Im nächsten Beispiel wird ein Funktions Objekt anstelle eines Lambda-Ausdrucks in Verbindung mit der **for_each** -Funktion verwendet, um die gleichen Ergebnisse wie in Beispiel 1 zu erzielen. In beiden Beispielen wird die Anzahl gerader Zahlen in einem `vector`-Objekt gespeichert. Um den Zustand des Vorgangs beizubehalten, wird die `FunctorClass`-Variable von der `m_evenCount`-Klasse mithilfe eines Verweises als Membervariable gespeichert. Um den Vorgang auszuführen, `FunctorClass` den Funktions Aufrufoperator **()** implementiert. Der Microsoft C++ -Compiler generiert Code, der in Größe und Leistung mit dem Lambda-Code in Beispiel 1 vergleichbar ist. Bei einem grundlegenden Problem, wie dem in diesem Artikel, ist der einfachere Lambda-Entwurf wahrscheinlich besser geeignet, als der Funktionsobjektentwurf. Wenn Sie allerdings der Meinung sind, die Funktionalität erfordere zukünftig möglicherweise beträchtliche Erweiterungen, verwenden Sie einen Funktionsobjektentwurf. Damit ist die Codeverwaltung einfacher.

Weitere Informationen zum- **Operator ()** finden Sie unter [Funktionsaufrufe](../cpp/function-call-cpp.md). Weitere Informationen zur **for_each** -Funktion finden Sie unter [for_each](../standard-library/algorithm-functions.md#for_each).

### <a name="code"></a>Code

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>Weitere Informationen

[Lambda-Ausdrücke](../cpp/lambda-expressions-in-cpp.md)<br/>
[Beispiele für Lambdaausdrücke](../cpp/examples-of-lambda-expressions.md)<br/>
[generate](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Ausnahmespezifikationen (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Compilerwarnung (Ebene 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Microsoft-spezifische Modifizierer](../cpp/microsoft-specific-modifiers.md)
