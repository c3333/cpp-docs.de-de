---
title: Compilerwarnung (Stufe 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 31deba2f421b461ba56d13810b5064b353a0e602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175674"
---
# <a name="compiler-warning-level-1-c4297"></a>Compilerwarnung (Stufe 1) C4297

„Funktion“: Die Funktion löst eine unerwartete Ausnahme aus

Eine Funktionsdeklaration enthält einen (möglicherweise impliziten) `noexcept` Spezifizierer, einen leeren `throw` ausnahmespezifizierer oder ein __declspec-Attribut [(nothrow)](../../cpp/nothrow-cpp.md) , und die Definition enthält eine oder mehrere [throw](../../cpp/try-throw-and-catch-statements-cpp.md) -Anweisungen. Um C4297 zu beheben, versuchen Sie nicht, Ausnahmen in Funktionen auszulösen, die als `__declspec(nothrow)`, `noexcept(true)` oder `throw()` deklariert sind. Alternativ können Sie die `noexcept`-, `throw()`- oder `__declspec(nothrow)`-Spezifikation entfernen.

Standardmäßig generiert der Compiler implizite `noexcept(true)`-Bezeichner für benutzerdefinierte Destruktoren und Deallocator-Funktionen und vom Compiler generierte spezielle Memberfunktionen. Dies entspricht dem ISO-Standard C++11. Um die Generierung impliziter noausgenommen-Spezifizierer zu verhindern und den Compiler auf das nicht standardmäßige Verhalten von Visual Studio 2013 zurückzusetzen, verwenden Sie die Option **/Zc: implicitnoaußer-** Compiler. Weitere Informationen finden Sie unter [/Zc: implicitnoaußer (implizite ausnahmespezifizierer)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Weitere Informationen zu Ausnahme Spezifikationen finden Sie unter [Ausnahme Spezifikationen (Throw)](../../cpp/exception-specifications-throw-cpp.md). Weitere Informationen zum Ändern des Verhaltens der Ausnahmebehandlung zur Kompilierzeit finden Sie auch unter [/eh (Ausnahme Behandlungsmodell)](../../build/reference/eh-exception-handling-model.md) .

Diese Warnung wird auch für __declspec ([dllexport](../../cpp/dllexport-dllimport.md))-Funktionen generiert, die als extern "C" gekennzeichnet sind C++ , auch wenn Sie Funktionen sind.

Im folgenden Beispiel wird C4297 generiert:

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```
