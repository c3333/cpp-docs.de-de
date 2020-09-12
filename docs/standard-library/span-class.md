---
title: Span-Klasse (C++-Standard Bibliothek) | Microsoft-Dokumentation
description: API-Referenz für die STL-spannen Klasse (Standard Template Library), die eine vereinfachte Ansicht für eine zusammenhängende Sequenz von Objekten bereitstellt.
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: 297104820f5498e59397db9025aed1675984a060
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039963"
---
# <a name="span-class-c-standard-library"></a>Span-Klasse (C++-Standard Bibliothek)

Stellt eine vereinfachte Ansicht für eine zusammenhängende Sequenz von-Objekten bereit. Eine Spanne stellt eine sichere Möglichkeit zum durchlaufen und Indizieren von Objekten dar, die im Arbeitsspeicher, wie z. b. in einem integrierten Array, oder gespeicherten Objekten, als Back-to-Back-Objekte angeordnet werden `std::array` `std::vector` .

Wenn Sie in der Regel mit einem Zeiger und einem Index auf eine Sequenz von Back-to-Back-Objekten zugreifen, stellt eine sicherere und einfachere `span` Alternative dar.

Die Größe eines `span` kann zur Kompilierzeit festgelegt werden, indem es als Vorlagen Argument angegeben wird, oder zur Laufzeit durch Angeben von `dynamic_extent` .

## <a name="syntax"></a>Syntax

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>Vorlagenparameter

`T`\
 Der Typ der Elemente in der Spanne.

`Extent`\
 Die Anzahl der Elemente in der Spanne, die zur Kompilierzeit angegeben werden. Andernfalls,  `std::dynamic_extent` Wenn die Anzahl der Elemente zur Laufzeit angegeben wird.

[ABLEITUNGS Handbuch](#deduction_guides)

## <a name="members"></a>Member

| **Typdefinitionen** | **Beschreibung** |
|-|-|
| [const_pointer](#pointer) | Der Typ eines Zeigers auf ein- **`const`** Element. |
| [const_reference](#reference) | Der Typ eines Verweises auf ein- **`const`** Element. |
| [difference_type](#difference_type) | Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen. |
| [element_type](#element_type) | Der Typ eines SPAN-Elements. |
| [Iterator](#iterator) | Der Typ eines Iterators für eine Spanne. |
| [Zeichner](#pointer) | Der Typ eines Zeigers auf ein Element. |
| [Referenz](#reference) | Der Typ eines Verweises auf ein Element. |
| [reverse_iterator](#reverse_iterator) | Der Typ eines umgekehrten Iterators für eine Spanne. |
| [size_type](#size_type) | Der Typ für das Ergebnis der Entfernung ohne Vorzeichen zwischen zwei Elementen in der Spanne. |
| [value_type](#value_type) | Der Typ eines Elements ohne- **`const`** oder- **`volatile`** Qualifikation. |
| **Konstruktoren** | **Beschreibung** |
|[Spanne](#span)| Erstellen Sie ein `span`.|
| **Iteratorunterstützung** | **Beschreibung** |
|[beginnen](#begin) | Einen Iterator, der auf das erste Element in der Spanne zeigt, wird erhalten.|
|[end](#end) | Einen Iterator, der auf das Ende der Spanne zeigt, wird erhalten. |
|[rbegin](#rbegin) | Rückgängigmachen eines umgekehrten Iterators, der auf das letzte Element der Spanne zeigt Das heißt, der Anfang der umgekehrten Spanne.|
|[rend](#rend) | Rückgängigmachen eines umgekehrten Iterators, der auf den Vordergrund der Spanne zeigt Das heißt, das Ende der umgekehrten Spanne.|
| **Zugriffs Elemente**| **Beschreibung** |
|[Zurück](#back) | Das letzte Element in der Spanne wird angezeigt.|
|[data](#data) | Die Adresse des ersten Elements in der Spanne erhalten.|
|[Beifahrer](#front) | Das erste Element in der Spanne wird angezeigt.|
|[KOM\[\]](#op_at) | Greift auf ein Element an einer angegebenen Position zu.|
| **Beobachter** | **Beschreibung** |
|[empty](#empty)| Überprüfen Sie, ob die Spanne leer ist.|
|[size](#size) | Gibt die Anzahl der Elemente in der Spanne an.|
|[size_bytes](#size_bytes) | Gibt die Größe der Spanne in Bytes an.|
| **Unter Ansichten** | **Beschreibung**|
| [first](#first_view) | Eine Teil Spanne von der Vorderseite der Spanne erhalten.|
| [last](#last_view) | Eine Teil Spanne von der Rückseite der Spanne erhalten.|
| [Teil Spanne](#sub_view) | Eine unter Spanne von einem beliebigen Ort in der Spanne erhalten.|
| **Operatoren** | **Beschreibung** |
|[span:: Operator =](#op_eq)| Ersetzen Sie die Spanne.|
|[span::-Operator\[\]](#op_at)| Das Element an der angegebenen Position. |

## <a name="remarks"></a>Bemerkungen

Alle Element Funktionen weisen eine `span` Konstante Zeit Komplexität auf.

Anders als `array` oder `vector` werden die darin enthaltenen Elemente von einem span-Element nicht "Besitzer". Eine Spanne gibt keinen Speicherplatz für die darin enthaltenen Elemente frei, da Sie nicht den Speicher für diese Objekte besitzt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<span>

**Namespace:** std

**Compileroption:** [/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md)

## <a name="spanback"></a><a name="back"></a> `span::back`

Das letzte Element in der Spanne wird angezeigt.

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte Element in der Spanne.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

Einen Iterator, der auf das erste Element in der Spanne zeigt, erhalten.

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf das erste Element in der Spanne zeigt.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

Einen Zeiger auf den Anfang der Span-Daten erhalten.

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Element, das in der Spanne gespeichert wird.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

Die Anzahl der Elemente zwischen zwei Elementen in einer Spanne.

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

Der Typ der Elemente in der Spanne.

```cpp
using element_type = T;
```

### <a name="remarks"></a>Bemerkungen

Der Typ wird `T` beim Erstellen einer Spanne aus dem Vorlagen Parameter entnommen.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

Gibt an, ob die Spanne Elemente enthält.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn `this->size() == 0` . Andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

Einen Iterator bis zum Ende der Spanne.

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der direkt hinter das Ende der Spanne zeigt.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Dereferenzieren Sie den von diesem Iterator zurückgegebenen Wert nicht. Verwenden Sie es, um zu ermitteln, ob der Iterator über das letzte Element in der Spanne hinaus erreicht wurde.

### <a name="example"></a>Beispiel

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

Hiermit wird eine Teil Spanne abgerufen, die von der Vorderseite dieser Spanne entnommen wird.

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der Elemente von der Vorderseite dieser Spanne, die in die Teil Spanne eingefügt werden soll.  
Die Anzahl der Elemente wird als Parameter für die Vorlage oder für die Funktion angegeben, wie unten gezeigt.

### <a name="return-value"></a>Rückgabewert

Eine Spanne, die `count` Elemente von der Vorderseite dieser Spanne enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die Vorlagen Version dieser Funktion, wenn dies möglich `count` ist, um zur Kompilierzeit zu überprüfen und Informationen über die Spanne beizubehalten, da Sie einen spannen Bereich mit fester Größe zurückgibt.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }

    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

Das erste Element in der Spanne wird angezeigt.

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das erste Element in der Spanne.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

Der Typ eines Iterators überspannen Elemente.

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>Bemerkungen

Dieser Typ dient als Iterator für die Elemente in einer Spanne.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

Erhalten Sie eine Teil Spanne, die vom Ende dieser Spanne entnommen wird.

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der Elemente vom Ende, die diese Spanne in die unter Spanne eingefügt werden soll.
Die Zahl kann wie unten dargestellt als Parameter für die Vorlage oder für die Funktion angegeben werden.

### <a name="return-value"></a>Rückgabewert

Eine Spanne, die die letzten `count` Elemente aus dieser Spanne enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die Vorlagen Version dieser Funktion, wenn dies möglich `count` ist, um zur Kompilierzeit zu überprüfen und Informationen über die Spanne beizubehalten, da Sie einen spannen Bereich mit fester Größe zurückgibt.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }

    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

Das Element in der Spanne an einer angegebenen Position.

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parameter

*kompensieren*\
NULL basiertes Element in der Spanne, auf das zugegriffen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Element am Positions *Offset*. Wenn die Position ungültig ist, ist das Verhalten nicht definiert.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

Weisen Sie dieser eine weitere Spanne zu.

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>Parameter

*außer*\
Die Spanne, die dieser zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Die Zuweisung bewirkt eine flache Kopie des Daten Zeigers und der Größe. Eine flache Kopie ist sicher, weil ein `span` keinen Speicher für die darin enthaltenen Elemente zuweist.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

Die Typen für einen Zeiger und einen **`const`** Zeiger auf ein span-Element.

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];

    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

Ein umgekehrter Iterator, der auf das letzte Element dieser Spanne zeigt, wird abgehandelt.

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang der umgekehrten Spanne zeigt.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

Die Typen für einen Verweis und ein **`const`** Verweis auf ein span-Element.

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

Erhalten Sie einen Iterator mit zufälligem Zugriff, der auf eine beliebige Breite hinter das Ende der umgekehrten Spanne zeigt.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter Iterator für den Platzhalter, der auf das letzte Element in der umgekehrten Spanne folgt. Das heißt, der Platzhalter vor dem ersten Element in der nicht umgekehrten Spanne.

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten Spanne verwendet, so wie [span:: End](#end) bei einer Spanne verwendet wird. Verwenden Sie es, um zu testen, ob ein umgekehrter Iterator das Ende seiner Spanne erreicht hat.

Der von zurückgegebene Wert `rend` darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

Der Typ eines umgekehrten Iterators für eine Spanne.

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

Gibt die Anzahl der Elemente in der Spanne an.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Spanne.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

Gibt die Größe der Elemente in der Spanne in Bytes an.

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Bytes, die alle Elemente in der Spanne belegen. Das heißt, `sizeof(element_type)` multipliziert mit der Anzahl der Elemente in der Spanne.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

Ein Typ ohne Vorzeichen, der zum Speichern der Anzahl von Elementen in einer Spanne geeignet ist.

```cpp
using size_type = size_t;
```

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span` Konstruktoren.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>Parameter

*r*\
Erstellen Sie eine Spanne aus einem Array.

*Countdown*\
Anzahl der Elemente, die sich in der Spanne befinden.

*erstes*\
Iterator zum ersten Element in der Spanne.

*letzten*\
Iterator, der unmittelbar hinter dem letzten Element in der Spanne liegt.

*Nr*\
Die Anzahl der Elemente, die sich in der Spanne befinden.

*außer*\
Erstellen Sie eine Kopie dieser Spanne.

*r*\
Erstellen Sie eine Spanne aus diesem Bereich.

### <a name="remarks"></a>Bemerkungen

Eine Spanne gibt keinen Speicher für Elemente in der Spanne frei, da Sie nicht die Speicherung der darin enthaltenen Objekte besitzt.

|Konstruktor  | BESCHREIBUNG  |
|---------|---------|
|`span()` | Erstellen Sie eine leere Spanne. Wird nur bei der Überladungs Auflösung berücksichtigt, wenn der Vorlagen Parameter `Extent` `0` oder ist `dynamic_extent` .|
|`span(It first, size_type count)` | Erstellen Sie eine Spanne aus den ersten `count` Elementen aus dem Iterator `first` .  Nur bei der Überladungs Auflösung berücksichtigt, wenn der Vorlagen Parameter `Extent` nicht ist `dynamic_extent` . |
|`span(It first, End last)` | Erstellen Sie eine Spanne aus den Elementen im Iterator, `first` bis das Ende `last` erreicht ist. Nur bei der Überladungs Auflösung berücksichtigt, wenn der Vorlagen Parameter `Extent` nicht ist `dynamic_extent` . `It` muss ein sein `contiguous_iterator` .  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  Erstellt eine Spanne aus `N` Elementen des angegebenen Arrays. Wird nur bei der Überladungs Auflösung berücksichtigt, wenn der Vorlagen Parameter `Extent` ist `dynamic_extent` oder entspricht `N` . |
|`span(R&& r)` |  Erstellen Sie eine Spanne aus einem Bereich. Ist nur an der Überladungs Auflösung beteiligt, wenn der Vorlagen Parameter `Extent` nicht `dynamic_extent` .|
|`span(const span& other)` |  Der vom Compiler generierte Kopierkonstruktor. Eine flache Kopie des Daten Zeigers ist sicher, da die Spanne den Speicher nicht zum Speichern der Elemente zuweist. |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | Konvertierungskonstruktor: erstellt eine Spanne aus einer anderen Spanne. Ist nur an der Überladungs Auflösung beteiligt, wenn der Vorlagen Parameter `Extent` ist `dynamic_extent` , oder `N` ist `dynamic_extent` oder ist oder entspricht `Extent` .|

### <a name="example"></a>Beispiel

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;

    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }

    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

Hiermit wird eine unter Spanne dieser Spanne erhalten.

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der Elemente, die in der Teil Spanne eingefügt werden sollen. Wenn `count` `dynamic_extent` (der Standardwert) ist, wird die Teil Spanne von bis zum `offset` Ende dieser Spanne entnommen.

*kompensieren*\
Die Position in dieser Spanne, an der die Teil Spanne gestartet werden soll.

### <a name="return-value"></a>Rückgabewert

Eine Spanne, beginnend bei `offset` in dieser Spanne. Enthält- `count` Elemente.

### <a name="remarks"></a>Bemerkungen

Eine Vorlagen Version dieser Funktion ist verfügbar, die die Anzahl zur Kompilierzeit überprüft, wodurch Informationen über die Spanne beibehalten werden, indem ein fester Wertebereich zurückgegeben wird.

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

Der Typ des Elements in der Spanne ohne- **`const`** oder- **`volatile`** Qualifikation.

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a> ABLEITUNGS Handbücher

Die folgenden ABLEITUNGS Handbücher werden für Span bereitgestellt.

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>Weitere Informationen

[\<span>](../standard-library/span.md)  
[Verwenden der Argument Ableitung für Klassen Vorlagen](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
