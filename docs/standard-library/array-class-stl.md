---
title: array-Klasse (C++-Standardbibliothek)| Microsoft-Dokumentation
ms.date: 11/13/2019
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
ms.openlocfilehash: 9cde21624e3a8d4cce6db9cdc054bad427340f31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203906"
---
# <a name="array-class-c-standard-library"></a>array-Klasse (C++-Standardvorlagenbibliothek)

Beschreibt ein Objekt, das eine Sequenz der Länge `N` aus Elementen des Typs `Ty` steuert. Die Sequenz ist als ein Array von `Ty` gespeichert, das im `array<Ty, N>`-Objekt enthalten ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|`Ty`|Der Typ eines Elements.|
|`N`|Die Anzahl der Elemente.|

## <a name="members"></a>Member

|Typendefinition|BESCHREIBUNG|
|-|-|
|[const_iterator](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[const_pointer](#const_pointer)|Der Typ eines konstanten Zeigers auf ein Element.|
|[const_reference](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[const_reverse_iterator](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[difference_type](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[Iterator](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[Zeichner](#pointer)|Der Typ eines Zeigers auf ein Element.|
|[Referenz](#reference)|Der Typ eines Verweises auf ein Element.|
|[reverse_iterator](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[size_type](#size_type)|Der Typ eines Abstands ohne Vorzeichen zwischen zwei Elementen.|
|[value_type](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[array](#array)|Erstellt ein Arrayobjekt.|
|[assign](#assign)|Veralteten. Verwenden Sie `fill` .) Ersetzt alle Elemente.|
|[at](#at)|Greift auf ein Element an einer angegebenen Position zu.|
|[Zurück](#back)|Greift auf das letzte Element zu.|
|[beginnen](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[cbegin](#cbegin)|Gibt einen für wahlfreien Zugriff eingerichteten konstanten Iterator auf das erste Element im Vektor zurück.|
|[cend](#cend)|Gibt einen für wahlfreien Zugriff eingerichteten konstanten Iterator zurück, der unmittelbar hinter das Ende des Vektors zeigt.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zum ersten Element in einem umgekehrten Array zurück.|
|[crend](#crend)|Gibt einen konstanten Iterator auf das Ende eines umgekehrten Arrays zurück.|
|[data](#data)|Ruft die Adresse des ersten Elements ab.|
|[empty](#empty)|Testet, ob Elemente vorhanden sind.|
|[end](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[erfüllen](#fill)|Ersetzt alle Elemente durch einen angegebenen Wert.|
|[Beifahrer](#front)|Greift auf das erste Element zu.|
|[max_size](#max_size)|Ermittelt die Anzahl von Elementen.|
|[rbegin](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[rend](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[size](#size)|Ermittelt die Anzahl von Elementen.|
|[swap](#swap)|Vertauscht den Inhalt von zwei Containern.|

|Operator|BESCHREIBUNG|
|-|-|
|[Array:: Operator =](#op_eq)|Ersetzt die kontrollierte Sequenz.|
|[Array::-Operator\[\]](#op_at)|Greift auf ein Element an einer angegebenen Position zu.|

## <a name="remarks"></a>Bemerkungen

Der Typ hat einen Standardkonstruktor `array()` und einen Standardzuweisungsoperator `operator=` und erfüllt die Anforderungen für ein `aggregate`. Daher können Objekte des Typs `array<Ty, N>` über einen Aggregatinitialisierer initialisiert werden. Beispiel:

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

erstellt das Objekt `ai`, das vier ganzzahlige Werte enthält, initialisiert die ersten drei Elemente mit den Werten 1, 2 und 3 und das vierte Element mit 0.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<array>

**Namespace:** std

## <a name="arrayarray"></a><a name="array"></a>Array:: Array

Erstellt ein Arrayobjekt.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Einzufügendes Objekt bzw. einzufügender Bereich.

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor `array()` bewirkt, dass die kontrollierte Sequenz nicht initialisiert (oder standardmäßig initialisiert) wird. Sie können ihn verwenden, um eine nicht initialisierte kontrollierte Sequenz festzulegen.

Der Kopierkonstruktor `array(const array& right)` Initialisiert die gesteuerte Sequenz mit der Sequenz [*right* `.begin()` , *right* `.end()` ). Sie können ihn verwenden, um eine initialisierte kontrollierte Sequenz festzulegen, die eine Kopie einer Sequenz ist, die vom Array-Objekt *right* kontrolliert wird.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arrayassign"></a><a name="assign"></a>Array:: Assign

In C++11 veraltet, wurde durch [fill](#fill) ersetzt. Ersetzt alle Elemente.

## <a name="arrayat"></a><a name="at"></a>Array:: at

Greift auf ein Element an einer angegebenen Position zu.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parameter

*abgeschrieben*\
Position des Elements, auf das zugegriffen wird

### <a name="remarks"></a>Bemerkungen

Die Member-Funktionen geben einen Verweis auf das Element der kontrollierten Sequenz an der Position *Off*zurück. Wenn diese Position ungültig ist, löst die Funktion ein Objekt der `out_of_range`-Klasse aus.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="arrayback"></a><a name="back"></a>Array:: Back

Greift auf das letzte Element zu.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben einen Verweis auf das letzte Element der kontrollierten Sequenz zurück, die nicht leer sein darf.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraybegin"></a><a name="begin"></a>Array:: begin

Legt den Anfang der kontrollierten Sequenz fest.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben einen Iterator mit wahlfreiem Zugriff zurück, der auf das erste Element der Sequenz zeigt (bzw. gerade über das Ende einer leeren Sequenz hinaus).

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraycbegin"></a><a name="cbegin"></a>Array:: cbegin

Gibt einen **`const`** Iterator zurück, der das erste Element im Bereich adressiert.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Random-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich `cbegin() == cend()` ).

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert `cbegin` können die Elemente im Bereich nicht geändert werden.

Sie können diese Memberfunktion anstelle der `begin()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `begin()` `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a>Array:: cend

Gibt einen **`const`** Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Random-Access-Iterator, der auf eine Position unmittelbar nach dem Ende des Bereichs verweist.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `end()` `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a>Array:: const_iterator

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als Iterator für den konstanten zufälligen Zugriff für die kontrollierte Sequenz dienen kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a>Array:: const_pointer

Der Typ eines konstanten Zeigers auf ein Element.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als konstanter Zeiger auf Elemente der Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reference"></a><a name="const_reference"></a>Array:: const_reference

Der Typ eines konstanten Verweises auf ein Element.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als Konstantenverweis für ein Element der gesteuerten Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>Array:: const_reverse_iterator

Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als konstanter umgekehrter Iterator für die kontrollierte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraycrbegin"></a><a name="crbegin"></a>Array:: crbegin

Gibt einen konstanten Iterator zum ersten Element in einem umgekehrten Array zurück.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein konstanter umgekehrter wahlfreier Zugriffsiterator, mit dem das erste Element in einem umgekehrten Array adressiert wird (bzw. mit dem das ehemals letzte Element im nicht umgekehrten Array adressiert wird).

### <a name="remarks"></a>Bemerkungen

Beim Rückgabewert von `crbegin` kann das Arrayobjekt nicht geändert werden.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="arraycrend"></a><a name="crend"></a>Array:: crend

Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element in einem umgekehrten Array nachfolgt.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein const_reverse-Iterator mit wahlfreiem Zugriff, der den Standort adressiert, der dem letzten Element in einem umgekehrten Array nachfolgt (der Speicherort, der dem ersten Element im nicht umgekehrten Array vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einem umgekehrten Array auf die gleiche Weise verwendet, wie [array::cend](#cend) bei einem Array verwendet wird.

Mit dem Rückgabewert von `crend` (entsprechend verringert) kann das Arrayobjekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende des Arrays von einem umgekehrten Iterator erreicht wurde.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="arraydata"></a><a name="data"></a>Array::d ATA

Ruft die Adresse des ersten Elements ab.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben die Adresse des ersten Elements der kontrollierten Sequenz zurück.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraydifference_type"></a><a name="difference_type"></a>Array::d ifference_type

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Ganzzahltyp mit Vorzeichen beschreibt ein Objekt, das die Differenz zwischen den Adressen von zwei beliebigen Elementen in der gesteuerten Sequenz darstellen kann. Es ist ein Synonym für den Typ `std::ptrdiff_t`.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
-4
```

## <a name="arrayempty"></a><a name="empty"></a>Array:: Empty

Testet, ob keine Elemente vorhanden sind.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt nur „true“ zurück, wenn `N == 0` gilt.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

    // display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
false
true
```

## <a name="arrayend"></a><a name="end"></a>Array:: End

Legt das Ende der kontrollierten Sequenz fest.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben einen Iterator mit wahlfreiem Zugriff zurück, der direkt hinter das Ende der Sequenz verweist.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayfill"></a><a name="fill"></a>Array:: Fill

Löscht ein Array und kopiert die angegebenen Elemente in das leere Array.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*ster*|Der Wert des Elements, das in das Array eingefügt wird.|

### <a name="remarks"></a>Bemerkungen

`fill` ersetzt jedes Element des Arrays mit dem angegebenen Wert.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a>Array:: Front

Greift auf das erste Element zu.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben einen Verweis auf das erste Element der kontrollierten Sequenz zurück, das nicht leer sein darf.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayiterator"></a><a name="iterator"></a>Array:: Iterator

Der Typ eines Iterators für die gesteuerte Sequenz.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als Iterator für zufälligen Zugriff für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3

it2: 0
```

## <a name="arraymax_size"></a><a name="max_size"></a>Array:: max_size

Ermittelt die Anzahl von Elementen.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `N` zurück.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayoperator"></a><a name="op_at"></a>Array:: Operator []

Greift auf ein Element an einer angegebenen Position zu.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parameter

*abgeschrieben*\
Position des Elements, auf das zugegriffen wird

### <a name="remarks"></a>Bemerkungen

Die Member-Funktionen geben einen Verweis auf das Element der kontrollierten Sequenz an der Position *Off*zurück. Wenn diese Position ungültig ist, ist das Verhalten nicht definiert.

Es ist auch eine nicht-Member- [Get](array-functions.md#get) -Funktion verfügbar, um einen Verweis auf ein Element eines **Arrays**zu erhalten.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
1 3
```

## <a name="arrayoperator"></a><a name="op_eq"></a>Array:: Operator =

Ersetzt die kontrollierte Sequenz.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator weist jedes Element von *right* dem entsprechenden Element der gesteuerten Sequenz zu und gibt dann zurück **`*this`** . Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arraypointer"></a><a name="pointer"></a>Array::p

Der Typ eines Zeigers auf ein Element.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als Zeiger auf Elemente der Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrbegin"></a><a name="rbegin"></a>Array:: rbegin

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben einen Rückwärtsiterator zurück, der an einen Punkt direkt hinter dem Ende der Sequenz verweist. Also wird damit der Anfang umgekehrten Sequenz angegeben.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayreference"></a><a name="reference"></a>Array:: Reference

Der Typ eines Verweises auf ein Element.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als Verweis auf ein Element der gesteuerten Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrend"></a><a name="rend"></a>Array:: rend

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen geben einen umgekehrten Iterator zurück, der auf das erste Element der Sequenz zeigt (bzw. gerade über das Ende einer leeren Sequenz hinaus). Also wird damit das Ende der umgekehrten Sequenz angegeben.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a>Array:: reverse_iterator

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Beschreibt ein Objekt, das als umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraysize"></a><a name="size"></a>Array:: size

Ermittelt die Anzahl von Elementen.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `N` zurück.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arraysize_type"></a><a name="size_type"></a>Array:: size_type

Der Typ eines Abstands ohne Vorzeichen zwischen zwei Elementen.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Bemerkungen

Der unsignierte Ganzzahltyp beschreibt ein Objekt, das die Länge jeder kontrollierten Sequenz darstellen kann. Es ist ein Synonym für den Typ `std::size_t`.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayswap"></a><a name="swap"></a>Array:: Swap

Tauscht den Inhalt dieses Arrays mit dem eines anderen aus.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die kontrollierten Sequenzen zwischen **`*this`** und *Rechts*aus. Sie führt verschiedene Elementzuweisungen und Konstruktoraufrufe proportional zu `N` durch.

Es ist auch eine [Swap](array-functions.md#swap) -Funktion ohne Member zum Austauschen von zwei **Array** Instanzen verfügbar.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="arrayvalue_type"></a><a name="value_type"></a>Array:: value_type

Der Typ eines Elements.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Ty` dar.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
        std::cout << " " << val;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>Weitere Informationen

[\<array>](../standard-library/array.md)
