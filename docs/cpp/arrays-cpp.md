---
title: Arrays (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: d4689162ea38f67b81c0f78bccba557cb40e78d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226033"
---
# <a name="arrays-c"></a>Arrays (C++)

Ein Array ist eine Sequenz von Objekten desselben Typs, die einen zusammenhängenden Speicherbereich belegen. Herkömmliche Arrays im C-Stil sind die Quelle vieler Fehler, sind aber immer noch üblich, insbesondere in älteren Codebasen. In modern C++ wird dringend empfohlen, [Std:: Vector](../standard-library/vector-class.md) oder [Std:: Array](../standard-library/array-class-stl.md) anstelle von Arrays im C-Stil zu verwenden, die in diesem Abschnitt beschrieben werden. Beide Standard Bibliothekstypen speichern ihre Elemente als zusammenhängenden Speicherblock, bieten jedoch viel größere Typsicherheit und Iteratoren, die sicher auf einen gültigen Speicherort innerhalb der Sequenz zeigen. Weitere Informationen finden Sie unter [Container (Modern C++)](containers-modern-cpp.md).

## <a name="stack-declarations"></a>Stapel Deklarationen

In einer C++-Array Deklaration wird die Array Größe nach dem Variablennamen und nicht nach dem Typnamen wie in anderen Sprachen angegeben. Im folgenden Beispiel wird ein Array mit 1000-Double-Wert deklariert, das auf dem Stapel zugeordnet werden soll. Die Anzahl der Elemente muss als Ganzzahlliteral oder anderweitig als konstanter Ausdruck angegeben werden, da der Compiler wissen muss, wie viel Stapel Speicher belegt werden muss. ein Wert, der zur Laufzeit berechnet wurde, kann nicht verwendet werden. Jedem Element im Array wird ein Standardwert von 0 zugewiesen. Wenn Sie keinen Standardwert zuweisen, enthält jedes Element anfänglich alle zufälligen Werte, die an diesem Speicherort vorkommen.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

Das erste Element im-Array ist das nullten-Element, und das letzte Element ist das (*n*-1)-Element, wobei *n* die Anzahl der Elemente ist, die das Array enthalten kann. Die Anzahl der Elemente in der Deklaration muss ein ganzzahliger Typ sein und muss größer als 0 sein. Es liegt in ihrer Verantwortung, sicherzustellen, dass das Programm niemals einen Wert an den Index Operator übergibt, der größer als ist `(size - 1)` .

Ein Array der Größe 0 (null) ist nur zulässig, wenn es sich bei dem Array um das letzte Feld in einem **`struct`** oder handelt **`union`** und wenn die Microsoft-Erweiterungen (/Ze) aktiviert sind.

Bei Stapel basierten Arrays ist die Zuordnungs-und Zugriffsgeschwindigkeit schneller als bei Heap basierten Arrays, aber die Anzahl von Elementen kann nicht so groß sein, dass zu viel Stapel Speicher verwendet wird. Wie viel zu groß ist, hängt von Ihrem Programm ab. Mit den Profil Erstellungs Tools können Sie bestimmen, ob ein Array zu groß ist.

## <a name="heap-declarations"></a>Heap Deklarationen

Wenn Sie ein Array benötigen, das zu groß für die Zuordnung im Stapel ist, oder dessen Größe zum Zeitpunkt der Kompilierung nicht bekannt sein kann, können Sie es mit einem [neuen \[ \] ](new-operator-cpp.md) Ausdruck auf dem Heap zuordnen. Der-Operator gibt einen Zeiger auf das erste Element zurück. Sie können den Index Operator mit der Zeiger Variablen genau wie bei einem Stapel basierten Array verwenden. Sie können auch die [Zeigerarithmetik](../c-language/pointer-arithmetic.md) verwenden, um den Zeiger auf beliebige Elemente im Array zu verschieben. Es liegt in ihrer Verantwortung, Folgendes sicherzustellen:

- Sie behalten immer eine Kopie der ursprünglichen Zeiger Adresse, sodass Sie den Arbeitsspeicher löschen können, wenn Sie das Array nicht mehr benötigen.
- Sie müssen die Zeiger Adresse nicht um die Array Grenzen hinaus erhöhen oder verringern.

Im folgenden Beispiel wird gezeigt, wie ein Array auf dem Heap zur Laufzeit definiert wird und wie mit dem Index Operator oder mithilfe von Zeigerarithmetik auf die Array Elemente zugegriffen wird:

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>Initialisieren von Arrays

Sie können ein Array in einer Schleife, ein Element gleichzeitig oder in einer einzelnen Anweisung initialisieren. Der Inhalt der beiden folgenden Arrays ist identisch:

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>Übergeben von Arrays an Funktionen

Wenn ein Array an eine Funktion übermittelt wird, wird es als Zeiger auf das erste Element übermittelt. Dies gilt sowohl für Stapel basierte als auch für Heap basierte Arrays. Der-Zeiger enthält keine zusätzlichen Größen-oder Typinformationen. Dieses Verhalten wird als *Zeiger Verfall*bezeichnet. Wenn Sie ein Array an eine Funktion übergeben, müssen Sie immer die Anzahl von Elementen in einem separaten Parameter angeben. Dieses Verhalten impliziert auch, dass die Array Elemente nicht kopiert werden, wenn das Array an eine Funktion übermittelt wird. Um zu verhindern, dass die-Funktion die Elemente ändert, geben Sie den-Parameter als Zeiger auf- **`const`** Elemente an.

Das folgende Beispiel zeigt eine Funktion, die ein Array und eine Länge akzeptiert. Der Zeiger verweist auf das ursprüngliche Array, nicht auf eine Kopie. Da der-Parameter nicht ist **`const`** , kann die-Funktion die Array Elemente ändern.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Deklarieren Sie das Array als "Konstanten", damit es innerhalb des Funktions Blocks schreibgeschützt ist:

```cpp
void process(const double p*, const size_t len);
```

Dieselbe Funktion kann auch auf diese Weise deklariert werden, ohne dass das Verhalten geändert werden muss. Das Array wird weiterhin als Zeiger auf das erste Element weitergegeben:

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>Mehrdimensionale Arrays

Bei Arrays, die von anderen Arrays erstellt werden, handelt es sich um mehrdimensionale Arrays. Diese mehrdimensionalen Arrays werden angegeben, indem nacheinander mehrere Konstantenausdrücke in Klammern gesetzt werden. Ein Beispiel ist diese Deklaration:

```cpp
int i2[5][7];
```

Er gibt ein Array vom Typ an **`int`** , das konzeptionell in einer zweidimensionalen Matrix von fünf Zeilen und sieben Spalten angeordnet ist, wie in der folgenden Abbildung dargestellt:

![Konzeptionelles Layout eines Multi&#45;dimensionalen Arrays](../cpp/media/vc38rc1.gif "Konzeptionelles Layout eines Multi&#45;dimensionalen Arrays") <br/>
Konzeptionelles Layout eines mehrdimensionalen Arrays

In Deklarationen von multidimensionalen Arrays, die über eine Initialisiererliste verfügen (wie in [Initialisierern](../cpp/initializers.md)beschrieben), kann der Konstante Ausdruck ausgelassen werden, der die Begrenzungen für die erste Dimension angibt. Beispiel:

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

Die vorhergehende Deklaration definiert ein Array, das aus vier Spalten mit je drei Zeilen besteht. Die Zeilen stellen Factorys dar und die Spalten Märkte, die von den Factorys beliefert werden. Die Werte entsprechen den Transportkosten von den Factorys zu den Märkten. Die erste Dimension des Arrays wird ausgelassen, aber der Compiler füllt sie aus, indem er den Initialisierer untersucht.

Die Verwendung des Dereferenzierungsoperators (*) für einen n-dimensionalen Arraytyp ergibt ein n-1-dimensionales Array. Wenn n 1 ist, ergibt sich ein Skalar (oder Arrayelement).

C++-Arrays werden in zeilengerichteter Reihenfolge gespeichert. Zeilengerichtete Reihenfolge bedeutet, dass sich der letzte Feldindex am schnellsten unterscheidet.

## <a name="example"></a>Beispiel

Die Möglichkeit des Umgehens von Begrenzungsspezifikationen für die erste Dimension eines mehrdimensionalen Arrays kann auch in Funktionsdeklarationen verwendet werden:

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

Die Funktion `FindMinToMkt` ist so geschrieben, dass das Hinzufügen von neuen Factorys keine Codeänderungen erfordert, sondern nur eine erneute Kompilierung.

## <a name="initializing-arrays"></a>Initialisieren von Arrays

Wenn eine Klasse über einen Konstruktor verfügt, werden Arrays dieser Klasse von einem Konstruktor initialisiert. Wenn weniger Elemente in der Initialisiererliste als Elemente im Array vorhanden sind, wird der Standardkonstruktor für die verbleibenden Elemente verwendet. Wenn kein Standardkonstruktor für die Klasse definiert wird, muss die Initialisiererliste abgeschlossen sein, d. h. es muss ein Initialisierer für jedes Element im Array vorhanden sein.

Betrachten Sie die `Point`-Klasse, die zwei Konstruktoren definiert:

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

Das erste Element von `aPoint` wird unter Verwendung des Konstruktors `Point( int, int )` erstellt; die verbleibenden zwei Elemente werden unter Verwendung des Standardkonstruktors erstellt.

Statische Member Arrays (ob **`const`** oder nicht) können in ihren Definitionen (außerhalb der Klassen Deklaration) initialisiert werden. Beispiel:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>Zugreifen auf Array Elemente

Sie können auf einzelne Elemente eines Arrays zugreifen, indem Sie den Arrayfeldindex-Operator (`[ ]`) verwenden. Wenn ein eindimensionales Array in einem Ausdruck ohne Feldindex verwendet wird, wird der Arrayname als Zeiger auf das ersten Element im Array ausgewertet.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Wenn Sie mehrdimensionale Arrays verwenden, können Sie verschiedene Kombinationen in Ausdrücken verwenden.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

Im vorangehenden Code `multi` ist ein dreidimensionales Array vom Typ **`double`** . Der `p2multi` Zeiger zeigt auf ein Array vom Typ **`double`** der Größe drei. In diesem Beispiel wird das Array mit einem, zwei oder drei Feldindizes verwendet. Obwohl im Allgemeinen alle Feldindizes angegeben werden, wie in der `cout`-Anweisung, ist es manchmal sinnvoll, eine bestimmte Teilmenge von Arrayelementen auszuwählen, wie in den Anweisungen gezeigt, die `cout` folgen.

## <a name="overloading-subscript-operator"></a>Überladen des Index Operators

Wie andere Operatoren kann der Index Operator ( `[]` ) vom Benutzer neu definiert werden. Das Standardverhalten des Indexoperators, wenn er nicht überladen ist, besteht darin, den Arraynamen und den Index unter Verwendung der folgenden Methode zu kombinieren:

`*((array_name) + (subscript))`

Wie bei allen Additionen, an denen Zeigertypen beteiligt sind, wird die Skalierung automatisch zur Anpassung an die Größe des Typs ausgeführt. Daher ist der resultierende Wert nicht *n* Bytes vom Ursprung von Array-Name; Vielmehr handelt es sich um das *n*-te Element des Arrays. Weitere Informationen zu dieser Konvertierung finden Sie unter [Additive Operatoren](additive-operators-plus-and.md).

Entsprechend wird die Adresse für mehrdimensionale Arrays anhand der folgenden Methode abgeleitet:

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>Arrays in Ausdrücken

Wenn ein Bezeichner eines Array Typs in einem anderen Ausdruck als **`sizeof`** , address-of ( `&` ) oder der Initialisierung eines Verweises auftritt, wird er in einen Zeiger auf das erste Array Element konvertiert. Beispiel:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Der Zeiger `psz` zeigt auf das erste Element des Arrays `szError1`. Arrays können im Gegensatz zu Zeigern keine änderbaren l-Werte sein. Daher ist die folgende Zuordnung ungültig:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Siehe auch

[Std:: Array](../standard-library/array-class-stl.md)
