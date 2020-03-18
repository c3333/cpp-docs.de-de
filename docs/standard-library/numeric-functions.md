---
title: '&lt;numeric&gt;-Funktionen'
description: Beschreibt die Funktions Vorlagen, die vom &lt;numerischen&gt;-Header in C++ der-Standard Bibliothek bereitgestellt werden.
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425364"
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt;-Funktionen

## <a name="accumulate"></a>Reichert

Berechnet die Summe aller Elemente in einem angegebenen Bereich, einschließlich eines Anfangs Werts, indem aufeinander folgende Teilsummen berechnet werden. Oder berechnet das Ergebnis von aufeinander folgenden partiellen Ergebnissen eines angegebenen binären Vorgangs.

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

### <a name="return-value"></a>Rückgabewert

Die Summe von *Init* und allen Elementen im angegebenen Bereich für die erste Vorlagen Funktion, oder für die zweite Vorlagen Funktion, das Ergebnis der Anwendung der binären Operation *Binary_Op* anstelle des Sum-Vorgangs auf (* PartialResult, *in_iter*), wobei *PartialResult* das Ergebnis früherer Anwendungen des Vorgangs ist und *in_iter* ein Iterator ist, der auf das nächste Element im Bereich zeigt.

### <a name="remarks"></a>Hinweise

Der Anfangswert stellt sicher, dass ein klar definiertes Ergebnis vorliegt, wenn der Bereich leer ist. in diesem Fall wird " *Init* " zurückgegeben. Der binäre Vorgang muss nicht assoziativ oder kommutativ sein. Das Ergebnis wird mit dem *anfänglichen Wert* initialisiert, und anschließend wird das *Ergebnis* = *Binary_Op*(*Result*, *in_iter*) iterativ durch den Bereich berechnet, wobei *in_iter* ein Iterator ist, der auf jedes aufeinanderfolgende Element im Bereich zeigt. Der Bereich muss gültig sein, und die Komplexität ist mit der Größe des Bereichs linear. Der Rückgabetyp des binären Operators muss in **Typ** konvertierbar sein, um Closure während der Iteration sicherzustellen.

### <a name="example"></a>Beispiel

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>adjacent_difference

Berechnet die aufeinander folgenden Unterschiede zwischen jedem Element und seinem Vorgänger in einem Eingabebereich. Gibt die Ergebnisse in einem Zielbereich aus. Oder berechnet das Ergebnis einer verallgemeinerten Prozedur, bei der der Differenz Vorgang durch einen anderen angegebenen binären Vorgang ersetzt wird.

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der das erste Element im Eingabebereich adressiert, dessen Elemente mit ihren jeweiligen Vorgängern differenziert werden sollen oder in dem die Wertpaare durch einen anderen angegebenen binären Vorgang verarbeitet werden sollen.

*Letzter*\
Ein Eingabeiterator, der das letzte Element im Eingabebereich adressiert, dessen Elemente mit ihren jeweiligen Vorgängern differenziert werden sollen oder in dem die Wertpaare durch einen anderen angegebenen binären Vorgang verarbeitet werden sollen.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Differenzen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Binary_Op*\
Der binäre Vorgang, der in der verallgemeinerten Operation angewendet werden soll, wobei der Vorgang der Subtraktion im differenzierenden Verfahren ersetzt wird.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der das Ende des Zielbereichs adressiert: `result` + (`last` - `first`).

### <a name="remarks"></a>Hinweise

Das *Ergebnis* des ausgabeiteratorergebnisses kann derselbe *Iterator sein*wie der eingabeiterator, damit `adjacent_difference` Werte direkt berechnet werden können.

Bei einer Sequenz von Werten *a*1, *a*2, *a*3 in einem Eingabebereich speichert die erste Vorlagen Funktion aufeinander folgende `adjacent_difference` Werte *a*1, *a*2- *a*1, a3- *a*2 im Zielbereich.

Bei einer Sequenz von Werten *a*1, *a*2, *a*3 in einem Eingabebereich speichert die zweite Vorlagen Funktion aufeinander folgende `adjacent_difference` Werte *a*1, *a*2 *Binary_Op* *a*1, *a*3 *Binary_Op* *a*2 im Zielbereich.

Der binäre Vorgang *Binary_Op* muss weder assoziativ noch kommutativ sein, da die Reihenfolge der angewendeten Vorgänge angegeben wird.

### <a name="example"></a>Beispiel

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="exclusive_scan"></a>exclusive_scan

Berechnet einen exklusiven Präfix-Sum-Vorgang, indem entweder `std::plus<>()` oder ein angegebener binärer Operator für einen Bereich verwendet wird, wenn ein Anfangswert angegeben wird. Schreibt die Ergebnisse in den Bereich, beginnend am angegebenen Ziel. Eine *exklusive Präfix* Summe bedeutet, dass das *n*-te Eingabe Element nicht in der *n*-ten Summe enthalten ist. Über Ladungen, die ein Ausführungsrichtlinien Argument enthalten, werden gemäß der angegebenen Richtlinie ausgeführt.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Summen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der das Ende des Zielbereichs adressiert: *Ergebnis* + (*Letztes* - *zuerst*).

## <a name="gcd"></a>GCD

Berechnet den größten gemeinsamen Divisor der ganzzahligen m und n.

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>Parameter

*m*, *n*\
Werte des ganzzahligen Typs.

### <a name="return-value"></a>Rückgabewert

Gibt den größten gemeinsamen Divisor der absoluten Werte von *m* und *n*zurück, oder 0 (null), wenn *m* und *n* NULL sind. Die Ergebnisse sind nicht definiert, wenn die absoluten Werte von *m* oder *n* nicht als Werte des Typs `common_type_t<M,N>`dargestellt werden können.

## <a name="inclusive_scan"></a>inclusive_scan

Berechnet einen inklusiven Präfix Summen Vorgang, indem entweder `std::plus<>()` oder ein angegebener binärer Operator für einen Bereich verwendet wird, wenn ein Anfangswert angegeben wird. Schreibt die Ergebnisse in den Bereich, beginnend am angegebenen Ziel. Ein *inklusives Präfix* Sum bedeutet, dass das *n*-te Eingabe Element in der *n*-ten Summe enthalten ist. Über Ladungen, die ein Ausführungsrichtlinien Argument enthalten, werden gemäß der angegebenen Richtlinie ausgeführt.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Summen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der das Ende des Zielbereichs adressiert: *Ergebnis* + (*Letztes* - *zuerst*).

## <a name="inner_product"></a>inner_product

Berechnet die Summe des elementweisen Produkts von zwei Bereichen und fügt sie einem angegebenen Anfangswert hinzu oder berechnet das Ergebnis einer allgemeinen Prozedur, in der die Summen- und Produktvorgänge durch andere angegebene binäre Vorgänge ersetzt werden.

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>Parameter

*First1*\
Ein Eingabeiterator, der das erste Element im ersten Bereich adressiert, dessen inneres oder generalisiertes inneres Produkt mit dem zweiten Bereich neu zu berechnen ist.

*Last1*\
Ein Eingabeiterator, der das letzte Element im ersten Bereich adressiert, dessen inneres oder generalisiertes inneres Produkt mit dem zweiten Bereich neu zu berechnen ist.

*First2*\
Ein Eingabeiterator, der das erste Element im zweiten Bereich adressiert, dessen inneres oder generalisiertes inneres Produkt mit dem ersten Bereich neu zu berechnen ist.

*Init* -\
Einen Anfangswert für den das innere oder generalisierte innere Produkt zwischen den Bereichen hinzugefügt wird.

*Binary_Op1*\
Der binäre Vorgang, der das innere Produkt des Summenvorgangs ersetzt, wird auf die elementweisen Produkte in der Generalisierung des inneren Produkts angewendet.

*Binary_Op2*\
Der binäre Vorgang, der das innere Produkt des elementweisen Produkt des Multiplizierungsvorgangs in der Generalisierung des inneren Produkts ersetzt.

### <a name="return-value"></a>Rückgabewert

Der erste Memberfunktion gibt die Summe des elementweisen Produkts zurück und fügt den angegebenen Anfangswert hinzu. Für Wertebereiche *a*i und *b*i wird folgendes zurückgegeben:

*Init* + (*a*1 \* *b*1) + (*a*2 \* *b*2) +... + (*a*n \* *b*n)

durch iteratives Ersetzen von *Init* durch *Init* + (*a*i \* *b*i).

Die zweite Memberfunktion gibt folgendes zurück:

*Init* *Binary_Op1* (*a*1 *Binary_Op2* *b*1) *Binary_Op1* (*a*2 *Binary_Op2* *b*2) *Binary_Op1* ... *Binary_Op1* (*a*n *Binary_Op2* *b*n)

durch iteratives Ersetzen von *Init* durch *Init* *Binary_Op1* (*a*i *Binary_Op2* *b*i).

### <a name="remarks"></a>Hinweise

Der Anfangswert stellt sicher, dass ein klar definiertes Ergebnis vorliegt, wenn der Bereich leer ist. In diesem Fall wird *Init* zurückgegeben. Die binären Operationen müssen nicht assoziativ oder kommutativ sein. Der Bereich muss gültig sein, und die Komplexität ist mit der Größe des Bereichs linear. Der Rückgabetyp des binären Operators muss in **Typ** konvertierbar sein, um Closure während der Iteration sicherzustellen.

### <a name="example"></a>Beispiel

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>Iota

Speichert einen Startwert, beginnend mit dem ersten Element und füllt mit aufeinander folgenden Schritten dieses Werts (`value++`) in jedem der Elemente im Intervall `[first,  last)`.

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Eingabeiterator, der das erste Element im aufzufüllenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der das letzte Element im aufzufüllenden Bereich adressiert.

*value*\
Der Anfangswert, der im ersten Element gespeichert werden soll, und, um für spätere Elemente nacheinander Inkrement zu erhöhen.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht einige Verwendungsmöglichkeiten für die `iota`-Funktion durch Ausfüllen einer [list](../standard-library/list.md) von ganzen Zahlen und Ausfüllen eines [vector](../standard-library/vector.md) mit `list`, damit die [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)-Funktion verwendet werden kann.

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="lcm"></a>LCM

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

Berechnet eine Reihe von Summen in einem Eingabebereich vom ersten Element bis zum *n*-ten Element und speichert das Ergebnis jeder solchen Summe im *n*-ten Element eines Zielbereichs. Oder berechnet das Ergebnis einer verallgemeinerten Prozedur, bei der der Sum-Vorgang durch einen anderen angegebenen binären Vorgang ersetzt wird.

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Eingabeiterator, der das erste Element in dem Bereich adressiert, der entsprechend eines angegebenen binären Vorgangs teilweise summiert oder kombiniert werden soll.

*Letzter*\
Ein Eingabeiterator, der das letzte Element in dem Bereich adressiert, der entsprechend eines angegebenen binären Vorgangs teilweise summiert oder kombiniert werden soll und eine Position nach dem letzten Element folgt, das tatsächlich im iterierten Sammelbereich enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Teilsummen gespeichert werden sollen, oder die aufeinander folgenden Ergebnisse des angegebenen binären Vorgangs.

*Binary_Op*\
Der binäre Vorgang, der in der verallgemeinerten Operation angewendet werden soll, wobei der Sum-Vorgang in der partiellen Sum-Prozedur ersetzt wird.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der das Ende des Zielbereichs adressiert: *Ergebnis* + (*Letztes* - *zuerst*).

### <a name="remarks"></a>Hinweise

Das *Ergebnis* des ausgabeiteratorergebnisses darf derselbe *Iterator sein*wie der eingabeiterator, damit partielle Summen direkt berechnet werden können.

Für eine Sequenz von Werten *a*1, *a*2,... *ein*x in einem Eingabebereich speichert die erste Vorlagen Funktion aufeinander folgende Teilsummen im Zielbereich. Das *n*-te Element wird durch angegeben (*a*1 + *a*2 + *a*3 +... + *a*n).

Bei einer Sequenz von Werten *a*1, *a*2, *a*3 in einem Eingabebereich speichert die zweite Vorlagen Funktion aufeinander folgende Teilergebnisse im Zielbereich. Das *n*-te Element wird von (() angegeben. ((*a*1 *Binary_Op* *a*2) *Binary_Op* *a*3) *Binary_Op* ...) *Binary_Op* *a*n).

Der binäre Vorgang *Binary_Op* muss weder assoziativ noch kommutativ sein, da die Reihenfolge der angewendeten Vorgänge angegeben wird.

### <a name="example"></a>Beispiel

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reduce"></a>Ver

Reduziert alle Elemente in einem angegebenen Bereich, möglicherweise einschließlich eines Anfangs Werts, indem Summen in einer beliebigen und möglicherweise permutenen Reihenfolge berechnet werden. Oder verringert, indem die Ergebnisse eines angegebenen binären Vorgangs berechnet werden. Über Ladungen, die ein Ausführungsrichtlinien Argument enthalten, werden gemäß der angegebenen Richtlinie ausgeführt.

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Summen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Anwendung *von Binary_Op* oder `std::plus<>()` *auf init* und alle Elemente im angegebenen Bereich auf (* PartialResult, *in_iter*), wobei *PartialResult* das Ergebnis früherer Anwendungen des Vorgangs ist, und *in_iter* ist ein Iterator, der auf ein Element im Bereich zeigt. In über Ladungen, die nicht *Init*angeben, entspricht der verwendete *Init* -Wert `typename iterator_traits<InputIterator>::value_type{}`.

### <a name="remarks"></a>Hinweise

`reduce` Verhalten ist nicht deterministisch, es sei denn, *Binary_Op* ist assoziativ und kommutativ. Das Verhalten ist nicht definiert, wenn *Binary_Op* ein beliebiges Element ändert oder einen Iterator im Intervall \[*First*, *Last*] (einschließlich) ungültig macht.

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

Wandelt die Elemente eines Bereichs mit einem angegebenen unären Operator um und berechnet dann einen exklusiven Präfix-Sum-Vorgang, indem entweder `std::plus<>()` oder ein angegebener binärer Operator für den Bereich verwendet wird, wenn ein Anfangswert angegeben wird. Schreibt die Ergebnisse in den Bereich, beginnend am angegebenen Ziel. Eine *exklusive Präfix* Summe bedeutet, dass das *n*-te Eingabe Element nicht in der *n*-ten Summe enthalten ist. Über Ladungen, die ein Ausführungsrichtlinien Argument enthalten, werden gemäß der angegebenen Richtlinie ausgeführt. Die Summe kann in beliebiger Reihenfolge ausgeführt werden.

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Summen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

*unary_op*\
Die unäre Operation, die auf jedes Element im angegebenen Bereich angewendet werden soll.

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

Wandelt die Elemente eines Bereichs mit einem angegebenen unären Operator um und berechnet dann einen inklusiven Präfix-Sum-Vorgang, indem entweder `std::plus<>()` oder ein angegebener binärer Operator für den Bereich verwendet wird, wenn ein Anfangswert angegeben wird. Schreibt die Ergebnisse in den Bereich, beginnend am angegebenen Ziel. Ein *inklusives Präfix* Sum bedeutet, dass das *n*-te Eingabe Element in der *n*-ten Summe enthalten ist. Über Ladungen, die ein Ausführungsrichtlinien Argument enthalten, werden gemäß der angegebenen Richtlinie ausgeführt. Die Summe kann in beliebiger Reihenfolge ausgeführt werden.

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Summen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

*unary_op*\
Die unäre Operation, die auf jedes Element im angegebenen Bereich angewendet werden soll.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

## <a name="transform_reduce"></a>transform_reduce

Transformiert einen Bereich von Elementen und wendet dann ein Funktor an, das die transformierten Elemente in beliebiger Reihenfolge reduziert. Effektiv, eine `transform` gefolgt von einer `reduce`.

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Parameter

*exec* -\
Eine Ausführungs Richtlinie.

*erste*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll.

*First1*\
Ein eingabeiterator, der das erste Element im Bereich adressiert, der mit *Binary_Op1*zusammengefasst oder kombiniert werden soll.

*Letzter*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Last1*\
Ein eingabeiterator, der das letzte Element in dem Bereich adressiert, der mit *Binary_Op1*zusammengefasst oder kombiniert werden soll. Dies ist eine Position hinter dem letzten Element, das tatsächlich in der iterierten Akkumulation enthalten ist.

*Ergebnis*\
Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Summen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.

*Init* -\
Ein Anfangswert, mit dem jedes Element wiederum mit *Binary_Op*hinzugefügt oder kombiniert wird.

*Binary_Op*\
Der binäre Vorgang, der auf jedes Element im angegebenen Bereich und das Ergebnis der vorherigen Anwendungen angewendet werden soll.

*unary_op*\
Die unäre Operation, die auf jedes Element im angegebenen Bereich angewendet werden soll.

### <a name="return-value"></a>Rückgabewert

Das transformierte und dann reduzierte Ergebnis.
