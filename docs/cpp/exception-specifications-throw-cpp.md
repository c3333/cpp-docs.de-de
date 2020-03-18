---
title: Ausnahme Spezifikationen (throw, noaußer) (C++)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 4c7cc6027a3af4c300b88389cb29e3ccf091514e
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509411"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Ausnahme Spezifikationen (throw, noaußer) (C++)

Ausnahme Spezifikationen sind ein C++ sprach Feature, das die Absicht des Programmierers in Bezug auf die Ausnahme Typen angibt, die von einer Funktion weitergegeben werden können. Mithilfe einer *Ausnahme Spezifikation*können Sie angeben, dass eine Funktion durch eine Ausnahme beendet werden kann oder nicht. Der Compiler kann diese Informationen verwenden, um Aufrufe der Funktion zu optimieren und das Programm zu beenden, wenn die Funktion durch eine unerwartete Ausnahme ausgelöst wird.

Vor c++ 17 gab es zwei Arten von Ausnahme Spezifikationen. Die *noaußer-Spezifikation* war neu in c++ 11. Gibt an, ob der Satz potenzieller Ausnahmen, die die Funktion mit Escapezeichen versehen können, leer ist. Die *dynamische Ausnahme Spezifikation*(or `throw(optional_type_list)` Specification) wurde in c++ 11 als veraltet markiert und in c++ 17 entfernt, mit Ausnahme von `throw()`, bei der es sich um einen Alias für `noexcept(true)`handelt. Diese Ausnahme Spezifikation wurde entworfen, um zusammenfassende Informationen darüber bereitzustellen, welche Ausnahmen aus einer Funktion heraus ausgelöst werden können, aber in der Praxis war sie problematisch. Die einzige dynamische Ausnahme Spezifikation, die sich als etwas nützlich erwiesen hat, war die Bedingungs `throw()` Spezifikation. Beispielsweise ist die Funktionsdeklaration:

```cpp
void MyFunction(int i) throw();
```

weist den Compiler an, dass die Funktion keine Ausnahmen auslöst. Im **/Std: c++ 14** -Modus kann dies jedoch zu undefiniertem Verhalten führen, wenn die Funktion eine Ausnahme auslöst. Daher wird empfohlen, anstelle des obigen Operators den [noaußer](../cpp/noexcept-cpp.md) -Operator zu verwenden:

```cpp
void MyFunction(int i) noexcept;
```

In der folgenden Tabelle ist die C++ Microsoft-Implementierung von Ausnahme Spezifikationen zusammengefasst:

|Ausnahmespezifikation|Bedeutung|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Die Funktion löst keine Ausnahme aus. Im Modus " [/Std: c++ 14](../build/reference/std-specify-language-standard-version.md) " (Standardeinstellung) sind `noexcept` und `noexcept(true)` Äquivalent. Wenn eine Ausnahme von einer Funktion ausgelöst wird, die `noexcept` oder `noexcept(true)`deklariert ist, wird " [Std::](../standard-library/exception-functions.md#terminate) End" aufgerufen. Wenn eine Ausnahme von einer Funktion ausgelöst wird, die im **/Std: c++ 14** -Modus als `throw()` deklariert wurde, ist das Ergebnis nicht definiertes Verhalten. Es wird keine bestimmte Funktion aufgerufen. Dies ist eine Abweichung vom c++ 14-Standard, die erfordert, dass der Compiler [Std:: Unexpected](../standard-library/exception-functions.md#unexpected)aufruft.  <br/> **Visual Studio 2017 Version 15,5 und**höher: im **/Std: c++ 17** -Modus sind die `noexcept`, `noexcept(true)`und `throw()` gleichwertig. Im **/Std: c++ 17** -Modus ist `throw()` ein Alias für `noexcept(true)`. Wenn im **/Std: c++ 17** -Modus eine Ausnahme von einer mit einer dieser Spezifikationen deklarierten Funktion ausgelöst wird, wird [Std::](../standard-library/exception-functions.md#terminate) End aufgerufen, wie vom c++ 17-Standard gefordert.|
|`noexcept(false)`<br/>`throw(...)`<br/>Keine Spezifikation|Die Funktion kann eine Ausnahme eines beliebigen Typs auslösen.|
|`throw(type)`| (**C++ 14 und früher**) Die-Funktion kann eine Ausnahme vom Typ `type`auslösen. Der Compiler akzeptiert die Syntax, interpretiert sie aber als `noexcept(false)`. Im **/Std: c++ 17** -Modus gibt der Compiler die Warnung C5040 aus.|

Wenn die Ausnahmebehandlung in einer Anwendung verwendet wird, muss eine Funktion in der aufrufsstapel vorhanden sein, die ausgelöste Ausnahmen behandelt, bevor Sie den äußeren Gültigkeitsbereich einer Funktion beenden, die als `noexcept`, `noexcept(true)`oder `throw()`gekennzeichnet ist. Wenn alle Funktionen, die zwischen dem, der eine Ausnahme auslöst, und der Ausnahme, die die Ausnahme behandelt, als `noexcept`angegeben werden, `noexcept(true)` (oder `throw()` im **/Std: c++ 17** -Modus), wird das Programm beendet, wenn die noaußer-Funktion die Ausnahme weitergibt.

Das Ausnahme Verhalten einer Funktion hängt von den folgenden Faktoren ab:

- Der [standardmäßige Kompilierungs Modus der Sprache](../build/reference/std-specify-language-standard-version.md) .
- Ob die Funktion mit C oder C++ kompiliert wird.

- Die [/eh](../build/reference/eh-exception-handling-model.md) -Compileroption, die Sie verwenden.

- Ob die Ausnahmespezifikation explizit angegeben wird.

Explizite Ausnahmespezifikationen sind für C-Funktionen nicht zulässig. Eine C-Funktion wird davon ausgegangen, dass keine Ausnahmen unter **/EHsc**ausgelöst werden, und kann unter **/EHS**, **/EHa**oder **/EHac**strukturierte Ausnahmen auslösen.

In der folgenden Tabelle wird zusammen C++ gefasst, ob eine Funktion möglicherweise unter verschiedenen Compilerausnahme-Behandlungsoptionen ausgelöst wird:

|Funktion|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|C++-Funktion ohne Ausnahmespezifikation|Ja|Ja|Ja|Ja|
|C++Funktion mit `noexcept`, `noexcept(true)`oder `throw()` Ausnahme Spezifikation|Nein|Nein|Ja|Ja|
|C++Funktion mit `noexcept(false)`, `throw(...)`oder `throw(type)` Ausnahme Spezifikation|Ja|Ja|Ja|Ja|

## <a name="example"></a>Beispiel

```cpp
// exception_specification.cpp
// compile with: /EHs
#include <stdio.h>

void handler() {
   printf_s("in handler\n");
}

void f1(void) throw(int) {
   printf_s("About to throw 1\n");
   if (1)
      throw 1;
}

void f5(void) throw() {
   try {
      f1();
   }
   catch(...) {
      handler();
    }
}

// invalid, doesn't handle the int exception thrown from f1()
// void f3(void) throw() {
//   f1();
// }

void __declspec(nothrow) f2(void) {
   try {
      f1();
   }
   catch(int) {
      handler();
    }
}

// only valid if compiled without /EHc
// /EHc means assume extern "C" functions don't throw exceptions
extern "C" void f4(void);
void f4(void) {
   f1();
}

int main() {
   f2();

   try {
      f4();
   }
   catch(...) {
      printf_s("Caught exception from f4\n");
   }
   f5();
}
```

```Output
About to throw 1
in handler
About to throw 1
Caught exception from f4
About to throw 1
in handler
```

## <a name="see-also"></a>Weitere Informationen

[try, throw, and catch Statements (C++) (try-, throw- und catch-Anweisungen (C++))](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Moderne C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md)