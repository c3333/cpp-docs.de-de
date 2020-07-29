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
ms.openlocfilehash: 1fa56ebf0a0358845ef620a89bc416992b3c0e31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221574"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Ausnahme Spezifikationen (throw, noaußer) (C++)

Ausnahme Spezifikationen sind eine C++ Language-Funktion, die die Absicht des Programmierers in Bezug auf die Ausnahme Typen angibt, die von einer Funktion weitergegeben werden können. Mithilfe einer *Ausnahme Spezifikation*können Sie angeben, dass eine Funktion durch eine Ausnahme beendet werden kann oder nicht. Der Compiler kann diese Informationen verwenden, um Aufrufe der Funktion zu optimieren und das Programm zu beenden, wenn die Funktion durch eine unerwartete Ausnahme ausgelöst wird.

Vor c++ 17 gab es zwei Arten von Ausnahme Spezifikationen. Die *noaußer-Spezifikation* war neu in c++ 11. Gibt an, ob der Satz potenzieller Ausnahmen, die die Funktion mit Escapezeichen versehen können, leer ist. Die *dynamische Ausnahme Spezifikation*(or `throw(optional_type_list)` Specification) wurde in c++ 11 als veraltet markiert und in c++ 17 entfernt, mit Ausnahme von, bei der es sich um `throw()` einen Alias für handelt `noexcept(true)` . Diese Ausnahme Spezifikation wurde entworfen, um zusammenfassende Informationen darüber bereitzustellen, welche Ausnahmen aus einer Funktion heraus ausgelöst werden können, aber in der Praxis war sie problematisch. Die einzige dynamische Ausnahme Spezifikation, die sich als etwas nützlich erwiesen hat, war die bedingungslose `throw()` Spezifikation. Beispielsweise ist die Funktionsdeklaration:

```cpp
void MyFunction(int i) throw();
```

weist den Compiler an, dass die Funktion keine Ausnahmen auslöst. Im **/Std: c++ 14** -Modus kann dies jedoch zu undefiniertem Verhalten führen, wenn die Funktion eine Ausnahme auslöst. Daher wird empfohlen, anstelle des obigen Operators den [noaußer](../cpp/noexcept-cpp.md) -Operator zu verwenden:

```cpp
void MyFunction(int i) noexcept;
```

In der folgenden Tabelle ist die Microsoft C++-Implementierung von Ausnahme Spezifikationen zusammengefasst:

|Ausnahmespezifikation|Bedeutung|
|-----------------------------|-------------|
|**`noexcept`**<br/>`noexcept(true)`<br/>`throw()`|Die Funktion löst keine Ausnahme aus. Im Modus " [/Std: c++ 14](../build/reference/std-specify-language-standard-version.md) " (Standardeinstellung) **`noexcept`** sind und `noexcept(true)` gleichwertig. Wenn eine Ausnahme von einer Funktion ausgelöst wird, die als **`noexcept`** oder deklariert ist `noexcept(true)` , wird " [Std::](../standard-library/exception-functions.md#terminate) End" aufgerufen. Wenn eine Ausnahme von einer Funktion ausgelöst wird `throw()` , die als im **/Std: c++ 14** -Modus deklariert ist, ist das Ergebnis nicht definiertes Verhalten. Es wird keine bestimmte Funktion aufgerufen. Dies ist eine Abweichung vom c++ 14-Standard, die erfordert, dass der Compiler [Std:: Unexpected](../standard-library/exception-functions.md#unexpected)aufruft.  <br/> **Visual Studio 2017 Version 15,5 und**höher: im **/Std: c++ 17** -Modus **`noexcept`** sind,, `noexcept(true)` und `throw()` gleichwertig. Im **/Std: c++ 17** -Modus `throw()` ist ein Alias für `noexcept(true)` . Wenn im **/Std: c++ 17** -Modus eine Ausnahme von einer mit einer dieser Spezifikationen deklarierten Funktion ausgelöst wird, wird [Std::](../standard-library/exception-functions.md#terminate) End aufgerufen, wie vom c++ 17-Standard gefordert.|
|`noexcept(false)`<br/>`throw(...)`<br/>Keine Spezifikation|Die Funktion kann eine Ausnahme eines beliebigen Typs auslösen.|
|`throw(type)`| (**C++ 14 und früher**) Die-Funktion kann eine Ausnahme vom Typ auslösen `type` . Der Compiler akzeptiert die Syntax, interpretiert sie aber als `noexcept(false)` . Im **/Std: c++ 17** -Modus gibt der Compiler die Warnung C5040 aus.|

Wenn die Ausnahmebehandlung in einer Anwendung verwendet wird, muss eine Funktion in der-aufrufsstapel vorhanden sein, die ausgelöste Ausnahmen behandelt, bevor Sie den äußeren Gültigkeitsbereich einer Funktion beenden, die als **`noexcept`** , oder gekennzeichnet ist `noexcept(true)` `throw()` . Wenn alle Funktionen aufgerufen werden, die zwischen dem, der eine Ausnahme auslöst, und dem, der die Ausnahme behandelt, als **`noexcept`** , `noexcept(true)` (oder `throw()` im **/Std: c++ 17** -Modus) aufgerufen wird, wird das Programm beendet, wenn die noaußer-Funktion die Ausnahme weitergibt.

Das Ausnahme Verhalten einer Funktion hängt von den folgenden Faktoren ab:

- Der [standardmäßige Kompilierungs Modus der Sprache](../build/reference/std-specify-language-standard-version.md) .
- Ob die Funktion mit C oder C++ kompiliert wird.

- Die [/eh](../build/reference/eh-exception-handling-model.md) -Compileroption, die Sie verwenden.

- Ob die Ausnahmespezifikation explizit angegeben wird.

Explizite Ausnahmespezifikationen sind für C-Funktionen nicht zulässig. Eine C-Funktion wird davon ausgegangen, dass keine Ausnahmen unter **/EHsc**ausgelöst werden, und kann unter **/EHS**, **/EHa**oder **/EHac**strukturierte Ausnahmen auslösen.

In der folgenden Tabelle wird zusammengefasst, ob eine C++-Funktion möglicherweise unter verschiedenen Compilerausnahme-Behandlungsoptionen auslöst:

|Funktion|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|C++-Funktion ohne Ausnahmespezifikation|Ja|Ja|Ja|Ja|
|C++-Funktion mit der **`noexcept`** `noexcept(true)` `throw()` Ausnahme Spezifikation, oder|Nein|Nein |Ja|Ja|
|C++-Funktion mit der `noexcept(false)` `throw(...)` `throw(type)` Ausnahme Spezifikation, oder|Ja|Ja|Ja|Ja|

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

[try-, throw- und catch-Anweisungen (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md)
