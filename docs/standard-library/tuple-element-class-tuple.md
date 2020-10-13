---
title: tuple_element-Klasse
ms.date: 11/04/2016
f1_keywords:
- utility/std::tuple_element
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
ms.openlocfilehash: be9d9fe56d35e96e4179eb511edccd475a369f32
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008292"
---
# <a name="tuple_element-class"></a>tuple_element-Klasse

Umschließt ein `tuple` -Element. Spezialisierungen umschließen `array`-Elemente und `pair`-Elemente.

## <a name="syntax"></a>Syntax

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Index des angegebenen Elements.

*Tupel*\
Der Typ des Tupels.

*Elem*\
Der Typ eines Arrayelements.

*Größe*\
Die Größe des Arrays.

*T1*\
Der Typ des ersten Elements in einem Paar.

*T2*\
Der Typ des zweiten Elements in einem Paar.

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage `tuple_element` verfügt über eine eingefügte typedef `type` , bei der es sich um ein Synonym für den Typ am Index *Index* des tupeltype- *Tupels*handelt.

Das Typedef `tuple_element_t` ist ein zweckmäßiger Alias für `tuple_element<Index, Tuple>::type`.

Die Klassen Vorlagen Spezialisierung für Arrays stellt eine Schnittstelle zu einem `array` als Tupel von `Size` Elementen bereit, von denen jedes denselben Typ aufweist. Jede Spezialisierung verfügt über eine eingefügte Typdefinition, `type` bei der es sich um ein Synonym für den Typ des *Index* Elements von handelt `array` , bei dem alle Konstanten konstant bleiben.

Die Vorlagenspezialisierungen für `pair`-Typen bieten eine einzelne Member-Typedef `type` an, die ein Synonym für den Typ des Elements an der angegebenen Position im Paar ist, wobei alle const- und/oder volatile-Qualifikationen beibehalten werden. Das Typedef `tuple_element_t` ist ein zweckmäßiger Alias für `tuple_element<N, pair<T1, T2>>::type`.

Verwenden Sie das [get &lt; Function &gt; Utility](../standard-library/utility-functions.md#get) , um das Element an einer angegebenen Position oder einem angegebenen Typ zurückzugeben.

## <a name="example-get-an-element-from-a-tuple"></a>Beispiel: Aufrufen eines Elements aus einem Tupel

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example-get-an-element-from-an-array"></a>Beispiel: Get a Element from a Array

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << e << " ";
    }
    cout << endl;

    // display first element "0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << val << endl;
}
```

```Output
0 1 2 3
0
```

## <a name="example-get-an-element-from-a-pair"></a>Beispiel: Get a Element from a pair

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents "0 1"
    cout << get<0>(c0) << " ";
    cout << get<1>(c0) << endl;

    // display first element "0 " by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << val << " ";

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << val2 << endl;
}
```

```Output
0 1.333
0 1.333
```

## <a name="requirements"></a>Anforderungen

**Header:**\<tuple>

**Header:** \<array> (für Array Spezialisierung)

**Header:** \<utility> (für paar Spezialisierung)

**Namespace:** std
