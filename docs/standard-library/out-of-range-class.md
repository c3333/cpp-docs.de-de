---
title: out_of_range-Klasse
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::out_of_range
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
ms.openlocfilehash: 3bbbc48aa2020782594606c6a53a34f7b937fc58
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521277"
---
# <a name="out_of_range-class"></a>out_of_range-Klasse

Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um ein Argument zu melden, dessen Wert außerhalb seines zulässigen Bereichs liegt.

## <a name="syntax"></a>Syntax

```cpp
class out_of_range : public logic_error {
public:
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};
```

## <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `what()` ist eine Kopie von `message.data()` . Weitere Informationen finden Sie unter [`what`](../standard-library/exception-class.md) und [`data`](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Beispiel

```cpp
// out_of_range.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

using namespace std;

int main() {
// out_of_range
   try {
      string str( "Micro" );
      string rstr( "soft" );
      str.append( rstr, 5, 3 );
      cout << str << endl;
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
   };
}
```

## <a name="output"></a>Ausgabe

```cpp
Caught: invalid string position
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<stdexcept>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Logic_error-Klasse](../standard-library/logic-error-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
