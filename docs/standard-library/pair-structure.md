---
title: pair-Struktur
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: 0a78d5074c37f4fbbfb736125626fa4b7fc7e275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505755"
---
# <a name="pair-structure"></a>pair-Struktur

Eine Struktur, die die Möglichkeit bietet, zwei Objekte als ein einzelnes Objekt zu behandeln.

## <a name="syntax"></a>Syntax

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    pair(const pair&) = default;
    pair(pair&&) = default;
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);

    template <class... Args1, class... Args2>
    pair(piecewise_construct_t, tuple<Args1...> first_args, tuple<Args2...> second_args);

    pair& operator=(const pair& p);
    template<class U1, class U2> pair& operator=(const pair<U1, U2>& p);
    pair& operator=(pair&& p) noexcept(see below );
    template<class U1, class U2> pair& operator=(pair<U1, U2>&& p);

    void swap(pair& p) noexcept(see below );
};

template<class T1, class T2>
    pair(T1, T2) -> pair<T1, T2>;
```

### <a name="parameters"></a>Parameter

*Wert1*\
Der Wert, der das erste Element von `pair` initialisiert.

*Wert2*\
Der Wert, der das zweite Element von `pair` initialisiert.

*Richting*\
Ein Paar, dessen Werte verwendet werden, um die Elemente eines anderen Paars zu initialisieren.

## <a name="return-value"></a>Rückgabewert

Der erste (standardmäßige) Konstruktor initialisiert das erste Element des Paars auf den Standardwert des Typs `T1` und das zweite Element auf den Standardwert des Typs `T2` .  Es ist definiert, wenn beide Typen standardmäßig konstruiert werden können.

Der zweite Konstruktor initialisiert das erste Element des Paars auf *Wert1* und das zweite auf *Wert2.*  Es ist definiert, wenn beide Typen kopierbar sind.

Der dritte (Vorlagen-) Konstruktor initialisiert das erste Element des Paars mit `Right` . der **erste** und der zweite in `Right` . **Zweitens**.  Es ist definiert, wenn beide Typen des Paars aus den bereitgestellten Werttypen konstruierbar sind.

Der vierte Konstruktor initialisiert das erste Element des Paars mit *Wert1* und das zweite auf *Wert2* mithilfe von [rvalue reference declarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).  Es ist definiert, wenn beide Typen des Paars aus den bereitgestellten Werttypen konstruierbar sind.

## <a name="remarks"></a>Bemerkungen

Die Vorlagen Struktur speichert ein paar von Objekten vom Typ `T1` `T2` bzw.. Der `first_type` -Typ ist identisch mit dem Vorlagen Parameter, `T1` und der-Typ `second_type` entspricht dem Vorlagen Parameter `T2` . `T1` und `T2` jeder benötigt nur einen Standardkonstruktor, einen Konstruktor mit einem einzelnen Argument und einen Dekonstruktor. Alle Member des Typs `pair` sind öffentlich, da der Typ als **`struct`** und nicht als deklariert wird **`class`** . Die beiden häufigsten Einsatzfälle für ein Paar sind, es als Rückgabetyp für eine Funktion zu verwenden, die zwei Werte zurückgibt, oder es als Element für die assoziativen Containerklassen [map-Klasse](../standard-library/map-class.md) und [multimap-Klasse](../standard-library/multimap-class.md) zu verwenden, die beide einen Schlüssel und einen Werttyp haben, die jedem Element zugeordnet sind. Letztere erfüllt die Anforderungen für einen paarweise assoziativen Container und hat einen Werttyp der Form `pair< const key_type, mapped_type >` .

## <a name="example"></a>Beispiel

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
```

```Output
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
```
