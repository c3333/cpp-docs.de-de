---
title: functional (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
ms.openlocfilehash: 2d06a92fea9a702633216e3244879687b66f97d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208727"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

Fügen Sie den STL/CLR-Header `<cliext/functional>` ein, um eine Reihe von Vorlagen Klassen und zugehörigen Vorlagen Delegaten und-Funktionen zu definieren.

## <a name="syntax"></a>Syntax

```
#include <functional>
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<cliext/funktionaler >

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Delegieren|BESCHREIBUNG|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|Delegat mit zwei Argumenten.|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Der Delegat mit zwei Argumenten gibt " **void**" zurück.|
|[unary_delegate (STL/CLR)](#unary_delegate)|Delegat mit einem Argument.|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|Ein Delegat mit einem Argument, der **void**zurückgibt.|

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|Ein Funktor zum negieren eines zwei-Argument-funktors.|
|[binder1st (STL/CLR)](#binder1st)|Funktor zum Binden des ersten Arguments an einen zwei-Argument-Funktor.|
|[binder2nd (STL/CLR)](#binder2nd)|Funktor, um das zweite Argument an einen zwei-Argument-Funktor zu binden.|
|[divides (STL/CLR)](#divides)|Funktor dividieren.|
|[equal_to (STL/CLR)](#equal_to)|Gleichheits Vergleichs-Funktor.|
|[greater (STL/CLR)](#greater)|Größerer Vergleichs Funktions tüktor.|
|[greater_equal (STL/CLR)](#greater_equal)|Größer oder gleich Vergleichs Funktions Vergleich.|
|[less (STL/CLR)](#less)|Weniger Vergleichs-Funktor.|
|[less_equal (STL/CLR)](#less_equal)|Kleiner oder gleicher Vergleichs Funktionswert.|
|[logical_and (STL/CLR)](#logical_and)|Logisches and-Funktor.|
|[logical_not (STL/CLR)](#logical_not)|Logisches NOT-Funktor.|
|[logical_or (STL/CLR)](#logical_or)|Logisches OR-Funktor.|
|[minus (STL/CLR)](#minus)|Subtract-Funktor.|
|[modulus (STL/CLR)](#modulus)|Modulus-Funktor.|
|[multiplies (STL/CLR)](#multiplies)|Funktor multiplizieren.|
|[negate (STL/CLR)](#negate)|Das Funktor, dessen Argument negiert zurückgegeben werden soll.|
|[not_equal_to (STL/CLR)](#not_equal_to)|Nicht gleicher Vergleichs-Functor.|
|[plus (STL/CLR)](#plus)|Funktor hinzufügen.|
|[unary_negate (STL/CLR)](#unary_negate)|Funktor zum negieren eines funktors mit einem Argument.|

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|Generiert ein binder1st-Element für ein Argument und einen Funktions tüktor.|
|[bind2nd (STL/CLR)](#bind2nd)|Generiert ein binder2nd-Element für ein Argument und einen Funktions tüktor.|
|[not1 (STL/CLR)](#not1)|Generiert eine unary_negate für ein Funktor.|
|[not2 (STL/CLR)](#not2)|Generiert eine binary_negate für ein Funktor.|

## <a name="members"></a>Members

## <a name="binary_delegate-stlclr"></a><a name="binary_delegate"></a>binary_delegate (STL/CLR)

Die Genereic-Klasse beschreibt einen Delegaten mit zwei Argumenten. Sie verwenden Sie, um einen Delegaten in Bezug auf die Argument-und Rückgabe Typen anzugeben.

### <a name="syntax"></a>Syntax

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parameter

*Arg1*<br/>
Der Typ des ersten Arguments.

*Arg2*<br/>
Der Typ des zweiten Arguments.

*Ergebnis*<br/>
Der Rückgabetyp.

### <a name="remarks"></a>Bemerkungen

Der Genereic-Delegat beschreibt eine Funktion mit zwei Argumenten.

Beachten Sie Folgendes für:

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

die Typen `Fun1` und `Fun2` sind Synonyme, für:

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

Sie weisen nicht denselben Typ auf.

### <a name="example"></a>Beispiel

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="binary_delegate_noreturn-stlclr"></a><a name="binary_delegate_noreturn"></a>binary_delegate_noreturn (STL/CLR)

Die Genereic-Klasse beschreibt einen Delegaten mit zwei Argumenten, der " **void**" zurückgibt. Sie verwenden Sie, um einen Delegaten in Bezug auf das Argument anzugeben.

### <a name="syntax"></a>Syntax

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parameter

*Arg1*<br/>
Der Typ des ersten Arguments.

*Arg2*<br/>
Der Typ des zweiten Arguments.

### <a name="remarks"></a>Bemerkungen

Der Genereic-Delegat beschreibt eine Funktion mit zwei Argumenten, die " **void**" zurückgibt.

Beachten Sie Folgendes für:

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

die Typen `Fun1` und `Fun2` sind Synonyme, für:

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

Sie weisen nicht denselben Typ auf.

### <a name="example"></a>Beispiel

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate-stlclr"></a><a name="binary_negate"></a>binary_negate (STL/CLR)

Die Vorlagen Klasse beschreibt einen Funktions tüktor, der, wenn er aufgerufen wird, das logische not seines gespeicherten funktors mit zwei Argumenten zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf seinen gespeicherten Funktor anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gen*<br/>
Der Typ des gespeicherten funktors.

## <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|
|stored_function_type|Der Typ des funktors.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|binary_negate|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^ ()|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt einen Funktions tüktor mit zwei Argumenten, der einen anderen zwei-Argument-Funktor speichert. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das logische Not des gespeicherten funktors, der mit den beiden Argumenten aufgerufen wird, zurückgegeben wird.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st-stlclr"></a><a name="bind1st"></a>bind1st (STL/CLR)

Generiert eine `binder1st` für ein Argument und einen Funktor.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>Vorlagenparameter

*Gebeut*<br/>
Der Typ des Arguments.

*Gen*<br/>
Der Typ des funktors.

#### <a name="function-parameters"></a>Funktionsparameter

*Funktionselement*<br/>
Der zu wrappende Funktor.

*left*<br/>
Das erste zu Umbruch Ende Argument.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`zurück. Sie verwenden Sie als bequeme Methode, um einen zwei-Argument-Funktor und das erste Argument in einem Funktor mit einem Argument zu wrappen, der ihn mit einem zweiten Argument aufruft.

### <a name="example"></a>Beispiel

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd-stlclr"></a><a name="bind2nd"></a>bind2nd (STL/CLR)

Generiert eine `binder2nd` für ein Argument und einen Funktor.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>Vorlagenparameter

*Gebeut*<br/>
Der Typ des Arguments.

*Gen*<br/>
Der Typ des funktors.

#### <a name="function-parameters"></a>Funktionsparameter

*Funktionselement*<br/>
Der zu wrappende Funktor.

*right*<br/>
Das zweite zu Umbruch Ende Argument.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`zurück. Sie verwenden Sie als bequeme Methode zum Einschließen eines funktors mit zwei Argumenten und des zweiten Arguments in einem Funktor mit einem Argument, der ihn mit einem ersten Argument aufruft.

### <a name="example"></a>Beispiel

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st-stlclr"></a><a name="binder1st"></a>binder1st (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument, das beim Aufrufen den gespeicherten Funktor mit zwei Argumenten zurückgibt, der mit seinem gespeicherten ersten Argument und dem angegebenen zweiten Argument aufgerufen wird. Sie verwenden es, um ein Funktions Objekt in Bezug auf seinen gespeicherten Funktor anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gen*<br/>
Der Typ des gespeicherten funktors.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|
|stored_function_type|Der Typ des funktors.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|binder1st|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^ ()|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument, das einen zwei-Argument-Funktor und ein erstes Argument speichert. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das Ergebnis des Aufrufs des gespeicherten funktors mit dem gespeicherten ersten Argument und dem angegebenen zweiten Argument zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd-stlclr"></a><a name="binder2nd"></a>binder2nd (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument, das beim Aufruf das gespeicherte Funktor mit zwei Argumenten mit dem angegebenen ersten Argument und dem gespeicherten zweiten Argument zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf seinen gespeicherten Funktor anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gen*<br/>
Der Typ des gespeicherten funktors.

## <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|
|stored_function_type|Der Typ des funktors.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|binder2nd|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^ ()|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument, das einen zwei-Argument-Funktor und ein zweites Argument speichert. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das Ergebnis des Aufrufs des gespeicherten funktors mit dem angegebenen ersten Argument und dem gespeicherten zweiten Argument zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides-stlclr"></a><a name="divides"></a>dividiert (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, das erste Argument zurückgibt, dividiert durch das zweite. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente und des Rückgabewerts.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|divides|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^ ()|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das erste Argument dividiert durch das zweite zurückgegeben wird.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to-stlclr"></a><a name="equal_to"></a>equal_to (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument gleich dem zweiten Argument ist. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|equal_to|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^ ()|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument gleich dem zweiten Argument ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater-stlclr"></a><a name="greater"></a>größer (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument größer als das zweite Argument ist. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|greater|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument größer als das zweite Argument ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal-stlclr"></a><a name="greater_equal"></a>Greater_equal (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument größer oder gleich dem zweiten Argument ist. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|greater_equal|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument größer oder gleich dem zweiten Argument ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less-stlclr"></a><a name="less"></a>Less (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument kleiner als das zweite Argument ist. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|less|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument kleiner als das zweite Argument ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal-stlclr"></a><a name="less_equal"></a>Less_equal (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument kleiner oder gleich dem zweiten Argument ist. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|less_equal|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument kleiner oder gleich dem zweiten Argument ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and-stlclr"></a><a name="logical_and"></a>logical_and (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktor, das beim Aufrufen von nur dann true zurückgibt, wenn sowohl das erste Argument als auch der zweite Test als true zurückgegeben werden. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|logical_and|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn sowohl das erste Argument als auch der zweite Test als true festgelegt ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not-stlclr"></a><a name="logical_not"></a>Logical_not (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das Argument entweder als false testet. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|argument_type|Der Typ des funktorarguments.|
|delegate_type|Der Typ des generischen Delegaten.|
|result_type|Der Typ des Funktions Ergebnisses.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|logical_not|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das Argument als false testet.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or-stlclr"></a><a name="logical_or"></a>Logical_or (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn entweder das erste Argument oder der zweite als true testet. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|logical_or|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn entweder das erste Argument oder der zweite als true testet.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus-stlclr"></a><a name="minus"></a>Minus (STL/CLR)

Die Vorlagen Klasse beschreibt einen Funktions tüktor, der, wenn er aufgerufen wird, das erste Argument abzüglich der zweiten zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente und des Rückgabewerts.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|minus|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das erste Argument abzüglich der zweiten zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus-stlclr"></a><a name="modulus"></a>Modulo (STL/CLR)

Die Vorlagen Klasse beschreibt einen Funktions tüktor, der, wenn er aufgerufen wird, das erste Argument Modulo der zweite zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente und des Rückgabewerts.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|modulus|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das erste Argument Modulo der zweite zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies-stlclr"></a><a name="multiplies"></a>multipliziert (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, das erste Argument Mal das zweite Argument zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente und des Rückgabewerts.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|multiplies|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das erste Argument der Sekunde zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate-stlclr"></a><a name="negate"></a>Negation (STL/CLR)

Die Vorlagen Klasse beschreibt einen Funktions tüktor, der, wenn er aufgerufen wird, sein Argument negiert zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|argument_type|Der Typ des funktorarguments.|
|delegate_type|Der Typ des generischen Delegaten.|
|result_type|Der Typ des Funktions Ergebnisses.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|negate|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, sein Argument negiert zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to-stlclr"></a><a name="not_equal_to"></a>Not_Equal_To (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument nicht gleich dem zweiten Argument ist. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|not_equal_to|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, nur dann true zurückgibt, wenn das erste Argument nicht gleich dem zweiten Argument ist.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1-stlclr"></a><a name="not1"></a>not1 (STL/CLR)

Generiert eine `unary_negate` für ein Funktor.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>Vorlagenparameter

*Gen*<br/>
Der Typ des funktors.

#### <a name="function-parameters"></a>Funktionsparameter

*Funktionselement*<br/>
Der zu wrappende Funktor.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Unary_negate (STL/CLR)-](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`zurück. Sie verwenden Sie als bequeme Methode zum Einbinden eines funktors mit einem Argument in einem Funktions tüktor, der seine logische Not-Methode bereitstellt.

### <a name="example"></a>Beispiel

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2-stlclr"></a><a name="not2"></a>not2 (STL/CLR)

Generiert eine `binary_negate` für ein Funktor.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>Vorlagenparameter

*Gen*<br/>
Der Typ des funktors.

#### <a name="function-parameters"></a>Funktionsparameter

*Funktionselement*<br/>
Der zu wrappende Funktor.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [binary_negate (STL/CLR)-](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`zurück. Sie verwenden Sie als bequeme Methode, um einen zwei-Argument-Funktions tüktor in einem Funktor zu wrappen, der seine logische Not-Methode bereitstellt.

### <a name="example"></a>Beispiel

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus-stlclr"></a><a name="plus"></a>Plus (STL/CLR)

Die Vorlagen Klasse beschreibt ein Funktionselement, das, wenn es aufgerufen wird, das erste Argument und das zweite zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ der Argumente und des Rückgabewerts.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|delegate_type|Der Typ des generischen Delegaten.|
|first_argument_type|Der Typ des ersten Arguments des functors.|
|result_type|Der Typ des Funktions Ergebnisses.|
|second_argument_type|Der Typ des zweiten funktors Arguments.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|Addition|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|Operator delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit zwei Argumenten. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das erste Argument zuzüglich der zweiten zurückgibt.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate-stlclr"></a><a name="unary_delegate"></a>unary_delegate (STL/CLR)

Die Genereic-Klasse beschreibt einen Delegaten mit einem Argument. Sie verwenden Sie, um einen Delegaten in Bezug auf die Argument-und Rückgabe Typen anzugeben.

### <a name="syntax"></a>Syntax

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ des Arguments.

*Ergebnis*<br/>
Der Rückgabetyp.

### <a name="remarks"></a>Bemerkungen

Der Genereic-Delegat beschreibt eine Funktion mit einem Argument.

Beachten Sie Folgendes für:

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

die Typen `Fun1` und `Fun2` sind Synonyme, für:

`delegate int Fun1(int);`

`delegate int Fun2(int);`

Sie weisen nicht denselben Typ auf.

### <a name="example"></a>Beispiel

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn-stlclr"></a><a name="unary_delegate_noreturn"></a>unary_delegate_noreturn (STL/CLR)

Die Genereic-Klasse beschreibt einen Delegaten mit einem Argument, der " **void**" zurückgibt. Sie verwenden Sie, um einen Delegaten in Bezug auf den Argumenttyp anzugeben.

### <a name="syntax"></a>Syntax

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>Parameter

*Gebeut*<br/>
Der Typ des Arguments.

### <a name="remarks"></a>Bemerkungen

Der Genereic-Delegat beschreibt eine Funktion mit einem Argument, die " **void**" zurückgibt.

Beachten Sie Folgendes für:

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

die Typen `Fun1` und `Fun2` sind Synonyme, für:

`delegate void Fun1(int);`

`delegate void Fun2(int);`

Sie weisen nicht denselben Typ auf.

### <a name="example"></a>Beispiel

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate-stlclr"></a><a name="unary_negate"></a>Unary_negate (STL/CLR)

Die Vorlagen Klasse beschreibt einen Funktions tüktor, der, wenn er aufgerufen wird, das logische not seines gespeicherten funktors mit einem Argument zurückgibt. Sie verwenden es, um ein Funktions Objekt in Bezug auf seinen gespeicherten Funktor anzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parameter

*Gen*<br/>
Der Typ des gespeicherten funktors.

### <a name="member-functions"></a>Elementfunktionen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|argument_type|Der Typ des funktorarguments.|
|delegate_type|Der Typ des generischen Delegaten.|
|result_type|Der Typ des Funktions Ergebnisses.|

|Member|BESCHREIBUNG|
|------------|-----------------|
|unary_negate|Erstellt das Funktor.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|Operator()|Berechnet die gewünschte Funktion.|
|delegate_type ^|Wandelt den Funktor in einen Delegaten um.|

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Klasse beschreibt ein Funktor mit einem Argument, in dem ein anderes Funktor mit einem Argument gespeichert wird. Sie definiert den Member-Operator `operator()` sodass, wenn das Objekt als Funktion aufgerufen wird, das logische Not des gespeicherten funktors, der mit dem-Argument aufgerufen wird, zurückgegeben wird.

Sie können das Objekt auch als Funktions Argument übergeben, dessen Typ `delegate_type^` ist und entsprechend konvertiert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```
