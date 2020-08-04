---
title: runtime_error-Klasse
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: a860e10994934ae0e97950fddb14e573f8752833
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520900"
---
# <a name="runtime_error-class"></a>runtime_error-Klasse

Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um Fehler zu melden, die mutmaßlich nur erkennbar sind, wenn das Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `what()` ist eine Kopie von `message.data()` . Weitere Informationen finden Sie unter [`what`](../standard-library/exception-class.md) und [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Beispiel

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<stdexcept>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Exception-Klasse](../standard-library/exception-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
