---
title: 'Gewusst wie: Abfangen von Ausnahmen, die von der MSIL ausgelöst wurden, in nativem Code'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 23adb573a62e93933c487f611c05aed4c08494ef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545084"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Gewusst wie: Abfangen von Ausnahmen, die von der MSIL ausgelöst wurden, in nativem Code

In nativem Code können Sie eine System C++ eigene Ausnahme von MSIL abfangen.  Sie können CLR-Ausnahmen mit `__try` und `__except`abfangen.

Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md) und [moderne C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Modul mit zwei Funktionen definiert, von denen eine native Ausnahme ausgelöst wird, und eine andere, die eine MSIL-Ausnahme auslöst.

```cpp
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Modul definiert, das eine native und eine MSIL-Ausnahme abfängt.

```cpp
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>Siehe auch

[Behandlung von Ausnahmen](../extensions/exception-handling-cpp-component-extensions.md)
