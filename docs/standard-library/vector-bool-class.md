---
title: vector&lt;bool&gt;-Klasse
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::flip
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: 4043b46bf2f93b362de029577fe9ac3c11dbcaa2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443921"
---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt;-Klasse

Die `vector<bool>`-Klasse ist eine partielle Spezialisierung von [Vector](../standard-library/vector-class.md) für Elemente des Typs **bool**. Sie verfügt über eine Zuweisung für den zugrunde liegenden Typ, der von der Spezialisierung verwendet wird, der die Speicherplatz Optimierung durch Speichern eines **booleschen** Werts pro Bit bereitstellt.

## <a name="syntax"></a>Syntax

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Bemerkungen

Diese Spezialisierung einer Klassenvorlage verhält sich wie vector, abgesehen von den Unterschieden, die in diesem Artikel erklärt werden.

Vorgänge mit dem **booleschen** Typ entsprechen den Werten im Container Speicher. `allocator_traits::construct` wird nicht verwendet, um diese Werte zu erstellen.

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[const_pointer](#const_pointer)|Eine Typedef für ein `const_iterator`-Element, das als konstanter Zeiger auf ein boolesches Element des `vector<bool>`-Elements dienen kann.|
|[const_reference](#const_reference)|Eine typedef für **bool**. Nach der Initialisierung werden keine Updates auf den ursprünglichen Wert berücksichtigt.|
|[pointer](#pointer)|Eine Typedef für ein `iterator`-Element, das als Zeiger auf ein boolesches Element des `vector<bool>`-Elements dienen kann.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[flip](#flip)|Kehrt alle Bits im `vector<bool>`-Element um.|
|[swap](#swap)|Tauscht die Elemente zweier `vector<bool>`n.|
|[operator[]](#op_at)|Gibt einen simulierten Verweis auf das `vector<bool>`-Element an einer angegebenen Position zurück.|
|`at`|Funktioniert genauso wie die nicht spezialisierte [vector::at](../standard-library/vector-class.md)-Funktion, mit der Ausnahme, dass die Proxyklasse [vector\<bool>::reference](#reference_class) verwendet wird. Informationen hierzu finden Sie unter [operator[]](#op_at).|
|`front`|Funktioniert genauso wie die nicht spezialisierte [vector::front](../standard-library/vector-class.md)-Funktion, mit der Ausnahme, dass die Proxyklasse [vector\<bool>::reference](#reference_class) verwendet wird. Informationen hierzu finden Sie unter [operator[]](#op_at).|
|`back`|Funktioniert genauso wie die nicht spezialisierte [vector::back](../standard-library/vector-class.md)-Funktion, mit der Ausnahme, dass die Proxyklasse [vector\<bool>::reference](#reference_class) verwendet wird. Informationen hierzu finden Sie unter [operator[]](#op_at).|

### <a name="proxy-class"></a>Proxyklasse

|||
|-|-|
|[vector\<bool>-Verweisklasse](#reference_class)|Eine Klasse, die als Proxy auftritt, um `bool&`-Verhalten zu simulieren, und deren Objekte Verweise auf Elemente (einzelne Bits) innerhalb eines `vector<bool>`-Objekts bereitstellen können.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: \<vector>

**Namespace:** std

## <a name="const_pointer"></a> vector\<bool>::const_pointer

Ein Typ, der ein Objekt beschreibt, das als konstanter Zeiger auf ein boolesches Element der Sequenz dienen kann, die im `vector<bool>`-Objekt enthalten ist.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a> vector\<bool>::const_reference

Ein Typ, der ein Objekt beschreibt, das als konstanter Verweis auf ein boolesches Element der Sequenz dienen kann, die im `vector<bool>`-Objekt enthalten ist.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen und Codebeispiele finden Sie unter [vector&lt;bool&gt;::reference::operator=](#reference_operator_eq).

## <a name="flip"></a> vector\<bool>::flip

Kehrt alle Bits in `vector<bool>` um.

```cpp
void flip();
```

### <a name="example"></a>Beispiel

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="op_at"></a> vector\<bool>::operator[]

Gibt einen simulierten Verweis auf das `vector<bool>`-Element an einer angegebenen Position zurück.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Pos*|Die Position des `vector<bool>`-Elements.|

### <a name="return-value"></a>Rückgabewert

Ein [vector\<bool>::reference](#reference_class)- oder [vector\<bool>::const_reference](#const_reference)-Objekt, das den Wert des indizierten Elements enthält.

Wenn die angegebene Position größer oder gleich der Größe des Containers ist, ist das Ergebnis nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn Sie mit _ITERATOR_DEBUG_LEVEL Satz kompilieren, tritt ein Laufzeitfehler auf, wenn Sie versuchen, auf ein Element außerhalb der Grenzen des Vektors zuzugreifen.  Weitere Informationen finden Sie unter [Checked Iterators (Überprüfte Iteratoren)](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

Dieses Codebeispiel zeigt die korrekte Verwendung von `vector<bool>::operator[]` und zwei häufige Codierungsfehler, die auskommentiert werden. Diese Fehler führen zu Fehlern, da die Adresse des `vector<bool>::reference` Objekts, das `vector<bool>::operator[]` zurückgibt, nicht verwendet werden kann.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="pointer"></a> vector\<bool>::pointer

Ein Typ, der ein Objekt beschreibt, das als Zeiger auf ein boolesches Element der Sequenz dienen kann, die im `vector<bool>`-Objekt enthalten ist.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a> vector\<bool>::reference-Klasse

Die `vector<bool>::reference`-Klasse ist eine Proxyklasse, die von der [vector\<bool>-Klasse](../standard-library/vector-bool-class.md) bereitgestellt wird, um `bool&` zu simulieren.

### <a name="remarks"></a>Bemerkungen

Ein simulierter Verweis ist erforderlich, da C++ systemintern keine direkten Verweise auf Bits zulässt. `vector<bool>` verwendet nur ein Bit pro Element, auf das anhand dieser Proxyklasse verwiesen werden kann. Allerdings ist die Verweissimulation nicht vollständig, da bestimmte Zuweisungen ungültig sind. Da die Adresse des `vector<bool>::reference`-Objekts beispielsweise nicht akzeptiert werden kann, ist der folgende Code, der [vector\<bool>::operator&#91;&#93;](#op_at) verwendet, nicht richtig:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a> vector\<bool>::reference::flip

Kehrt den booleschen Wert eines [vector\<bool>](../standard-library/vector-bool-class.md)-Elements um, auf das verwiesen wird.

```cpp
void flip();
```

#### <a name="example"></a>Beispiel

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

###  <a name="reference_operator_bool"></a> vector\<bool>::reference::operator bool

Stellt eine implizite Konvertierung von `vector<bool>::reference` in **bool**bereit.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Rückgabewert

Der boolesche Wert des Elements des vector\<bool>-Objekts.

#### <a name="remarks"></a>Bemerkungen

Das `vector<bool>`-Objekt kann von diesem Operator nicht geändert werden.

###  <a name="reference_operator_eq"></a> vector\<bool>::reference::operator=

Weist einen booleschen Wert einem Bit zu oder weist den Wert, der in einem Element enthalten ist, auf das verwiesen wird, einem Bit zu.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Der Elementverweis, dessen Wert dem Bit zugewiesen werden soll.

*Val* -\
Der boolesche Wert, der dem Bit zugewiesen werden soll.

#### <a name="example"></a>Beispiel

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="swap"></a> vector\<bool>::swap

Statische Memberfunktion, die zwei Elemente mit booleschen Vektoren ( `vector<bool>`) mithilfe der Proxyklasse [vector\<bool>::reference](#reference_class) austauscht.

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das Element, das mit dem *richtigen* Element ausgetauscht werden soll.

*Rechte*\
Das Element, das mit dem *linken* Element ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Überladung unterstützt die besonderen Proxyanforderungen von `vector<bool>`. [vector::swap](../standard-library/vector-class.md) bietet die gleiche Funktionalität wie die Überladung von `vector<bool>::swap()` mit einem Argument.

## <a name="see-also"></a>Weitere Informationen

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
