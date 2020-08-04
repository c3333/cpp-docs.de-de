---
title: overflow_error-Klasse
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::overflow_error
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
ms.openlocfilehash: b0bc3fc01dced3daf68c0b25ef1b68ea3f624761
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521225"
---
# <a name="overflow_error-class"></a>overflow_error-Klasse

Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen arithmetischen Überlauf zu melden.

## <a name="syntax"></a>Syntax

```cpp
class overflow_error : public runtime_error {
public:
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};
```

## <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `what()` ist eine Kopie von `message.data()` . Weitere Informationen finden Sie unter [`what`](../standard-library/exception-class.md) und [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Beispiel

```cpp
// overflow_error.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 33 > bitset;
      bitset[32] = 1;
      bitset[0] = 1;
      unsigned long x = bitset.to_ulong( );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bitset<N> overflow
Type class std::overflow_error
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<stdexcept>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Runtime_error-Klasse](../standard-library/runtime-error-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
