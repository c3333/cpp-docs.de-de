---
title: 'Vorgehensweise: Abfangen von Ausnahmen in nativem Code, die von MSIL ausgelöst wurden'
description: Beispiele für das Abfangen von Ausnahmen in System eigenem Code, der von MSIL ausgelöst wird.
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: b68a771d27e091f86331703b55bc2eb52dfbb41b
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898577"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Vorgehensweise: Abfangen von Ausnahmen in nativem Code, die von MSIL ausgelöst wurden

In System eigenem Code können Sie die native C++-Ausnahme von MSIL erfassen.  Sie können CLR-Ausnahmen mit **`__try`** und abfangen **`__except`** .

Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md) und [moderne C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example-1"></a>Beispiel 1

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

## <a name="example-2"></a>Beispiel 2

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

## <a name="see-also"></a>Weitere Informationen

[Ausnahmebehandlung](../extensions/exception-handling-cpp-component-extensions.md)
