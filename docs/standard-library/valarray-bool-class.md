---
title: valarray&lt;bool&gt;-Klasse
ms.date: 11/04/2016
f1_keywords:
- valarray<bool>
- valarray/std::valarray<bool>
helpviewer_keywords:
- valarray<bool> class
ms.assetid: fc0e7121-4758-4ea5-86c3-f04448f04acf
ms.openlocfilehash: 9145a6c75850fec78ca821b236133cc6c38beda9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215425"
---
# <a name="valarrayltboolgt-class"></a>valarray&lt;bool&gt;-Klasse

Eine spezialisierte Version des **Valarray \<Type> ** -Klassen Vorlagen Elements für Elemente des Typs **`bool`** .

## <a name="syntax"></a>Syntax

```cpp
class valarray<bool>
```

## <a name="example"></a>Beispiel

```cpp
// valarray_bool.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaBool ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
   for ( i = 0 ; i < 10 ; i++ )
      cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
   for ( i = 0 ; i < 10 ; i++ )
      cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBool = ( vaL < vaR );
   cout << "The result of the less-than comparison "
   << "test is the\nvalarray<bool>: ( ";
   for ( i = 0 ; i < 10 ; i++ )
      cout << vaBool [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The result of the less-than comparison test is the
valarray<bool>: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<valarray>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Valarray-Klasse](../standard-library/valarray-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
