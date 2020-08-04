---
title: underflow_error-Klasse
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::underflow_error
helpviewer_keywords:
- underflow_error class
ms.assetid: d632f1f9-9c6c-4954-b96b-03041bfab22d
ms.openlocfilehash: 3f521e8ec083cd158212b3ae9cb9fcf26edc7e76
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520511"
---
# <a name="underflow_error-class"></a>underflow_error-Klasse

Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen arithmetischen Unterlauf zu melden.

## <a name="syntax"></a>Syntax

```cpp
class underflow_error : public runtime_error {
public:
    explicit underflow_error(const string& message);

    explicit underflow_error(const char *message);

};
```

## <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `what()` ist eine Kopie von `message.data()` . Weitere Informationen finden Sie unter [`what`](../standard-library/exception-class.md) und [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Beispiel

```cpp
// underflow_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      throw underflow_error( "The number's a bit small, captain!" );
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The number's a bit small, captain!
Type: class std::underflow_error
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<stdexcept>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Runtime_error-Klasse](../standard-library/runtime-error-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
