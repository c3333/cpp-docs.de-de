---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320289"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Fügen Sie den `<cliext/utility>` STL/CLR-Header `pair` ein, um die Vorlagenklasse und mehrere unterstützende Vorlagenfunktionen zu definieren.

## <a name="syntax"></a>Syntax

```cpp
#include <utility>
```

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<cliext/utility>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Umschließen Sie ein Paar von Elementen.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[Operator == (Paar) (STL/CLR)](#op_eq)|Paar gleichen Vergleich.|
|[Operator!= (Paar) (STL/CLR)](#op_neq)|Paar nicht gleich Vergleich.|
|[Operator< (Paar) (STL/CLR)](#op_lt)|Paar weniger als Vergleich.|
|[Operator\<= (Paar) (STL/CLR)](#op_lteq)|Paar weniger als oder gleich Vergleich.|
|[Operator> (Paar) (STL/CLR)](#op_gt)|Paar größer als Vergleich.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Paar größer als oder gleich Vergleich.|

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Erstellen Sie ein Paar aus einem Paar von Werten.|

## <a name="members"></a>Member

## <a name="pair-stlclr"></a><a name="pair"></a>Paar (STL/CLR)

Die Vorlagenklasse beschreibt ein Objekt, das ein Wertpaar umschließt.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parameter

*Wert1*<br/>
Der Typ des ersten umschlossenen Werts.

*Wert2*<br/>
Der Typ des zweiten umschlossenen Werts.

## <a name="members"></a>Member

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|Der Typ des ersten umschlossenen Werts.|
|[pair::second_type (STL/CLR)](#second_type)|Der Typ des zweiten umschlossenen Werts.|

|Member-Objekt|BESCHREIBUNG|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|Der erste gespeicherte Wert.|
|[pair::second (STL/CLR)](#second)|Der zweite gespeicherte Wert.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Erstellt ein Paarobjekt.|
|[pair::swap (STL/CLR)](#swap)|Tauscht den Inhalt von zwei Paaren.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Ersetzt das gespeicherte Wertepaar.|

## <a name="remarks"></a>Bemerkungen

Das Objekt speichert ein Wertpaar. Mit dieser Vorlagenklasse können Sie zwei Werte in einem einzelnen Objekt kombinieren. Außerdem speichert `cliext::pair` das Objekt (hier beschrieben) nur verwaltete Typen. , um ein Paar nicht `std::pair`verwalteter `<utility>`Typen zu speichern, verwenden Sie in .

## <a name="pairfirst-stlclr"></a><a name="first"></a>Paar::erste (STL/CLR)

Der erste umschlossene Wert.

### <a name="syntax"></a>Syntax

```cpp
Value1 first;
```

### <a name="remarks"></a>Bemerkungen

Das Objekt speichert den ersten umschlossenen Wert.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>Paar::first_type (STL/CLR)

Der Typ des ersten umschlossenen Werts.

### <a name="syntax"></a>Syntax

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter *Value1*.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>Paar::Operator= (STL/CLR)

Ersetzt das gespeicherte Wertepaar.

### <a name="syntax"></a>Syntax

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Paar zum Kopieren.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator kopiert *das Recht* `*this`auf das Objekt und gibt dann zurück. Sie verwenden es, um das gespeicherte Wertepaar durch eine Kopie des gespeicherten Wertepaares *rechts*zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>Paar::pAir (STL/CLR)

Erstellt ein Paarobjekt.

### <a name="syntax"></a>Syntax

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Paar zu speichern.

*val1*<br/>
Erster zu speichernder Wert.

*val2*<br/>
Zweiter zu speichernder Wert.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`pair();`

initialisiert das gespeicherte Paar mit standardmäßig konstruierten Werten.

Der Konstruktor:

`pair(pair<Value1, Value2>% right);`

initialisiert das gespeicherte `right.`Paar mit [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) und `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

initialisiert das gespeicherte `right->`Paar mit [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) und `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

Der Konstruktor:

`pair(Value1 val1, Value2 val2);`

initialisiert das gespeicherte Paar mit *val1* und *val2*.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a>Paar::Sekunde (STL/CLR)

Der zweite umschlossene Wert.

### <a name="syntax"></a>Syntax

```cpp
Value2 second;
```

### <a name="remarks"></a>Bemerkungen

Das Objekt speichert den zweiten umschlossenen Wert.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>Paar::second_type (STL/CLR)

Der Typ des zweiten umschlossenen Werts.

### <a name="syntax"></a>Syntax

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter *Value2*.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a>Paar::Swap (STL/CLR)

Tauscht den Inhalt von zwei Paaren.

### <a name="syntax"></a>Syntax

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Koppeln, um Inhalte mit zu tauschen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht das gespeicherte Wertepaar zwischen `*this` und *rechts*aus.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair (STL/CLR)

Erstellen `pair` Sie eine aus einem Paar von Werten.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parameter

*Wert1*<br/>
Der Typ des ersten umschlossenen Werts.

*Wert2*<br/>
Der Typ des zweiten umschlossenen Werts.

*first*<br/>
Erster zu umschließender Wert.

*second*<br/>
Zweiter zu umschließender Wert.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `pair<Value1, Value2>(first, second)` zurück. Sie verwenden es, `pair<Value1, Value2>` um ein Objekt aus einem Paar von Werten zu erstellen.

### <a name="example"></a>Beispiel

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>Operator!= (Paar) (STL/CLR)

Paar nicht gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linkes Paar zum Vergleichen.

*Richting*<br/>
Rechtes Paar zu vergleichen.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(left == right)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht gleich *rechts* angeordnet ist, wenn die beiden Paare Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>Operator&lt; (Paar) (STL/CLR)

Paar weniger als Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linkes Paar zum Vergleichen.

*Richting*<br/>
Rechtes Paar zu vergleichen.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`gibt zurück. Sie verwenden es, um zu testen, ob *links* vor *rechts* angeordnet ist, wenn die beiden Paare Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>Operator&lt;= (Paar) (STL/CLR)

Paar weniger als oder gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linkes Paar zum Vergleichen.

*Richting*<br/>
Rechtes Paar zu vergleichen.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(right < left)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht nach *rechts* sortiert ist, wenn die beiden Paare Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>Operator == (Paar) (STL/CLR)

Paar gleichen Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linkes Paar zum Vergleichen.

*Richting*<br/>
Rechtes Paar zu vergleichen.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `left.first ==` `right.first &&` `left.second ==` `right.second`gibt zurück. Sie verwenden es, um zu testen, ob *links* gleich *rechts* angeordnet ist, wenn die beiden Paare Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>Operator&gt; (Paar) (STL/CLR)

Paar größer als Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linkes Paar zum Vergleichen.

*Richting*<br/>
Rechtes Paar zu vergleichen.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `right` `<` `left`gibt zurück. Sie verwenden es, um zu testen, ob *links* nach *rechts* sortiert ist, wenn die beiden Paare Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>Operator&gt;= (Paar) (STL/CLR)

Paar größer als oder gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linkes Paar zum Vergleichen.

*Richting*<br/>
Rechtes Paar zu vergleichen.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(left < right)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht vor *rechts* angeordnet ist, wenn die beiden Paare Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
