---
title: Arrays (C++)
description: Erfahren Sie, wie Sie den nativen Arraytyp in der Programmiersprache Standard C++ deklarieren und verwenden.
ms.date: 11/08/2020
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 2a84e5db04d0a37ebd65e0d979e9b075b7c23312
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381583"
---
# <a name="arrays-c"></a>Arrays (C++)

Ein Array ist eine Sequenz von Objekten desselben Typs, die einen zusammenhängenden Speicherbereich belegen. Herkömmliche Arrays im C-Stil sind die Quelle vieler Fehler, sind aber immer noch üblich, insbesondere in älteren Codebasen. In modern C++ wird dringend empfohlen, [Std:: Vector](../standard-library/vector-class.md) oder [Std:: Array](../standard-library/array-class-stl.md) anstelle von Arrays im C-Stil zu verwenden, die in diesem Abschnitt beschrieben werden. Beide Standard Bibliothekstypen speichern ihre Elemente als zusammenhängenden Speicherblock. Allerdings bieten Sie viel größere Typsicherheit und unterstützen Iteratoren, die sicher auf einen gültigen Speicherort innerhalb der Sequenz zeigen. Weitere Informationen finden Sie unter [Container](../standard-library/stl-containers.md).

## <a name="stack-declarations"></a>Stapel Deklarationen

In einer C++-Array Deklaration wird die Array Größe nach dem Variablennamen und nicht nach dem Typnamen wie in anderen Sprachen angegeben. Im folgenden Beispiel wird ein Array mit 1000-Double-Wert deklariert, das auf dem Stapel zugeordnet werden soll. Die Anzahl der Elemente muss als Ganzzahlliteral oder else als konstanter Ausdruck angegeben werden. Das liegt daran, dass der Compiler wissen muss, wie viel Stapel Speicher belegt werden muss. ein Wert, der zur Laufzeit berechnet wird, kann nicht verwendet werden. Jedem Element im Array wird ein Standardwert von 0 zugewiesen. Wenn Sie keinen Standardwert zuweisen, enthält jedes Element anfänglich alle zufälligen Werte, die sich an diesem Speicherort befinden.

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

Das erste Element im-Array ist das nullte-Element. Das letzte Element ist das ( *n* -1)-Element, wobei *n* die Anzahl der Elemente ist, die das Array enthalten kann. Die Anzahl der Elemente in der Deklaration muss ein ganzzahliger Typ sein und muss größer als 0 sein. Es liegt in ihrer Verantwortung, sicherzustellen, dass das Programm niemals einen Wert an den Index Operator übergibt, der größer als ist `(size - 1)` .

Ein Array der Größe 0 (null) ist nur zulässig, wenn das Array das letzte Feld in einem **`struct`** oder ist **`union`** und wenn die Microsoft-Erweiterungen aktiviert sind ( **`/Za`** oder **`/permissive-`** nicht festgelegt sind).

Stapel basierte Arrays sind schneller Zuordnungs-und Zugriffsberechtigungen als Heap basierte Arrays. Der Stapel Speicher ist jedoch begrenzt. Die Anzahl von Array Elementen kann nicht so groß sein, dass Sie zu viel Stapel Arbeitsspeicher verwendet. Wie viel zu groß ist, hängt von Ihrem Programm ab. Mit den Profil Erstellungs Tools können Sie bestimmen, ob ein Array zu groß ist.

## <a name="heap-declarations"></a>Heap Deklarationen

Möglicherweise benötigen Sie ein Array, das zu groß ist, um auf dem Stapel zuzuordnen, oder dessen Größe zum Zeitpunkt der Kompilierung nicht bekannt ist. Es ist möglich, dieses Array mithilfe eines-Ausdrucks dem Heap zuzuordnen [`new[]`](new-operator-cpp.md) . Der-Operator gibt einen Zeiger auf das erste Element zurück. Der Index Operator funktioniert wie bei einem Stapel basierten Array mit der Zeiger Variablen. Sie können auch die [Zeigerarithmetik](../c-language/pointer-arithmetic.md) verwenden, um den Zeiger auf beliebige Elemente im Array zu verschieben. Es liegt in ihrer Verantwortung, Folgendes sicherzustellen:

- Sie behalten immer eine Kopie der ursprünglichen Zeiger Adresse, sodass Sie den Arbeitsspeicher löschen können, wenn Sie das Array nicht mehr benötigen.
- Sie müssen die Zeiger Adresse nicht um die Array Begrenzungen erhöhen oder verringern.

Im folgenden Beispiel wird gezeigt, wie ein Array auf dem Heap zur Laufzeit definiert wird. Es zeigt, wie Sie mithilfe des Index Operators und mithilfe von Zeigerarithmetik auf die Array Elemente zugreifen können:

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

Wenn ein Array an eine Funktion übermittelt wird, wird es als Zeiger auf das erste Element, egal ob es sich um ein Stapel basiertes oder ein Heap basiertes Array handelt. Der-Zeiger enthält keine zusätzlichen Größen-oder Typinformationen. Dieses Verhalten wird als *Zeiger Verfall* bezeichnet. Wenn Sie ein Array an eine Funktion übergeben, müssen Sie immer die Anzahl von Elementen in einem separaten Parameter angeben. Dieses Verhalten impliziert auch, dass die Array Elemente nicht kopiert werden, wenn das Array an eine Funktion übermittelt wird. Um zu verhindern, dass die-Funktion die Elemente ändert, geben Sie den-Parameter als Zeiger auf- **`const`** Elemente an.

Das folgende Beispiel zeigt eine Funktion, die ein Array und eine Länge akzeptiert. Der Zeiger verweist auf das ursprüngliche Array, nicht auf eine Kopie. Da der-Parameter nicht **`const`** ist, kann die-Funktion die Array Elemente ändern.

```cpp
void process(double *p, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Deklarieren und definieren Sie den Array Parameter als schreibgeschützt `p` **`const`** innerhalb des Funktions Blocks:

```cpp
void process(const double *p, const size_t len);
```

Dieselbe Funktion kann auch auf diese Weise deklariert werden, ohne dass das Verhalten geändert werden muss. Das Array wird weiterhin als Zeiger auf das erste Element weitergegeben:

```cpp
// Unsized array
void process(const double p[], const size_t len);

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

Sie können mehrdimensionale Arrays deklarieren, die über eine Initialisiererliste verfügen (siehe [Initialisierer](../cpp/initializers.md)). In diesen Deklarationen kann der Konstante Ausdruck, der die Begrenzungen für die erste Dimension angibt, ausgelassen werden. Zum Beispiel:

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

Sie können auch die Begrenzungen-Spezifikation für die erste Dimension eines mehrdimensionalen Arrays in Funktions Deklarationen weglassen, wie hier gezeigt:

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

Die-Funktion `FindMinToMkt` wird so geschrieben, dass das Hinzufügen neuer Factorys keine Codeänderungen erfordert, sondern lediglich eine Neukompilierung.

## <a name="initializing-arrays"></a>Initialisieren von Arrays

Arrays von Objekten, die über einen Klassenkonstruktor verfügen, werden vom Konstruktor initialisiert. Wenn in der Initialisiererliste weniger Elemente als Elemente im Array vorhanden sind, wird der Standardkonstruktor für die verbleibenden Elemente verwendet. Wenn kein Standardkonstruktor für die Klasse definiert ist, muss die Initialisiererliste *Fertig* sein, d. h., es muss ein Initialisierer für jedes Element im Array vorhanden sein.

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

Statische Member Arrays (ob **`const`** oder nicht) können in ihren Definitionen (außerhalb der Klassen Deklaration) initialisiert werden. Zum Beispiel:

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

Sie können auf einzelne Elemente eines Arrays zugreifen, indem Sie den Arrayfeldindex-Operator (`[ ]`) verwenden. Wenn Sie den Namen eines eindimensionalen Arrays ohne einen Index verwenden, wird er als Zeiger auf das erste Element des Arrays ausgewertet.

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

Im vorangehenden Code `multi` ist ein dreidimensionales Array vom Typ **`double`** . Der `p2multi` Zeiger zeigt auf ein Array vom Typ **`double`** der Größe drei. In diesem Beispiel wird das Array mit einem, zwei oder drei Feldindizes verwendet. Obwohl es häufiger üblich ist, alle abonniert anzugeben, wie in der `cout` -Anweisung, ist es manchmal sinnvoll, eine bestimmte Teilmenge von Array Elementen auszuwählen, wie in den folgenden Anweisungen dargestellt `cout` .

## <a name="overloading-subscript-operator"></a>Überladen des Index Operators

Wie andere Operatoren kann der Index Operator ( `[]` ) vom Benutzer neu definiert werden. Das Standardverhalten des Indexoperators, wenn er nicht überladen ist, besteht darin, den Arraynamen und den Index unter Verwendung der folgenden Methode zu kombinieren:

`*((array_name) + (subscript))`

Wie bei allen Addition, die Zeiger Typen umfasst, erfolgt die Skalierung automatisch, um die Größe des Typs anzupassen. Der resultierende Wert ist nicht *n* Bytes vom Ursprung von `array_name` , sondern das *n* -te Element des Arrays. Weitere Informationen zu dieser Konvertierung finden Sie unter [Additive Operatoren](additive-operators-plus-and.md).

Entsprechend wird die Adresse für mehrdimensionale Arrays anhand der folgenden Methode abgeleitet:

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>Arrays in Ausdrücken

Wenn ein Bezeichner eines Array Typs in einem anderen Ausdruck als **`sizeof`** , address-of ( `&` ) oder der Initialisierung eines Verweises auftritt, wird er in einen Zeiger auf das erste Array Element konvertiert. Zum Beispiel:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Der Zeiger `psz` zeigt auf das erste Element des Arrays `szError1`. Arrays können im Gegensatz zu Zeigern keine änderbaren l-Werte sein. Daher ist die folgende Zuweisung unzulässig:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Siehe auch

[Std:: Array](../standard-library/array-class-stl.md)
