---
title: length_error-Klasse
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::length_error
helpviewer_keywords:
- length_error class
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
ms.openlocfilehash: 740ae69948a8f1975872f223ba51fb669121a891
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520887"
---
# <a name="length_error-class"></a>length_error-Klasse

Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen Versuch zu melden, ein Objekt zu erstellen, das zu lang ist, um angegeben werden zu können.

## <a name="syntax"></a>Syntax

```cpp
class length_error : public logic_error {
public:
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};
```

## <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `what()` ist eine Kopie von `message.data()` . Weitere Informationen finden Sie unter [`what`](../standard-library/exception-class.md) und [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Beispiel

```cpp
// length_error.cpp
// compile with: /EHsc /GR /MDd
#include <vector>
#include <iostream>

using namespace std;

template<class  T>
class stingyallocator : public allocator< T>
{
public:
   template <class U>
      struct rebind { typedef stingyallocator<U> other; };
   _SIZT max_size( ) const
   {
         return 10;
   };

};

int main( )
{
   try
   {
      vector<int, stingyallocator< int > > myv;
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught vector<T> too long
Type class std::length_error
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<stdexcept>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Logic_error-Klasse](../standard-library/logic-error-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
