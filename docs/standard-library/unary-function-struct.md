---
title: unary_function-Struktur
ms.date: 11/04/2016
f1_keywords:
- functional/std::unary
helpviewer_keywords:
- unary_function class
ms.assetid: 04c2fbdc-c1f6-48ed-b6cc-292a6d484627
ms.openlocfilehash: a38a22abe4381afd45948e56d46c54f39028517d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217375"
---
# <a name="unary_function-struct"></a>unary_function-Struktur

Eine leere Basisstruktur, mit der Typen definiert werden, die möglicherweise von abgeleiteten Klassen geerbt werden, die ein unäres Funktionsobjekt bereitstellt.

## <a name="syntax"></a>Syntax

```cpp
struct unary_function
{
   typedef Arg argument_type;
   typedef Result result_type;
};
```

## <a name="remarks"></a>Bemerkungen

Die Vorlagen Struktur fungiert als Basis für Klassen, die eine Member-Funktion der Form **result_type** `operator()` ( **constargument_type&**) definieren **`const`** .

Alle diese abgeleiteten unären Funktionen können auf ihren einzigen Argumenttyp als **argument_type** und ihren Rückgabetyp als **result_type** verweisen.

## <a name="example"></a>Beispiel

```cpp
// functional_unary_function.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan10: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 10);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greaterthan10());
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
```
