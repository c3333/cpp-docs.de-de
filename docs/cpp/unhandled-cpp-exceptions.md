---
title: Nicht behandelte C++-Ausnahmen
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: 48b417c48a3cbb903f3fabaf31b1423e79a1a414
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233586"
---
# <a name="unhandled-c-exceptions"></a>Nicht behandelte C++-Ausnahmen

Wenn für die aktuelle Ausnahme kein übereinstimmender Handler (oder ein **`catch`** Auslassungs Zeichen Handler) gefunden werden kann, wird die vordefinierte `terminate` Lauf Zeitfunktion aufgerufen. (Sie können auch explizit `terminate` in einem ihrer Handler aufzurufen.) Die Standardaktion von `terminate` ist das aufzurufen `abort` . Wenn `terminate` eine andere Funktion in Ihrem Programm aufrufen soll, bevor Sie die Anwendung beenden, rufen Sie die `set_terminate`-Funktion mit dem Funktionsnamen auf, der als sein einzelnes Argument aufgerufen werden soll. Sie können `set_terminate` an jedem Punkt im Programm aufrufen. Die- `terminate` Routine ruft immer die letzte Funktion auf, die als Argument für angegeben wurde `set_terminate` .

## <a name="example"></a>Beispiel

Das folgende Beispiel löst eine `char *`-Ausnahme aus, aber es enthält keinen Handler, der dazu vorgesehen ist, Ausnahmen des Typs `char *` zu erfassen. Der Aufruf von `set_terminate` weist `terminate` an, `term_func` aufzurufen.

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>Output

```Output
term_func was called by terminate.
```

Die `term_func`-Funktion muss das Programm oder den aktuellen Thread beenden, idealerweise mit dem Aufruf von `exit`. Wenn stattdessen eine Rückkehr zum Aufruf erfolgt, wird `abort` aufgerufen.

## <a name="see-also"></a>Siehe auch

[Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)
