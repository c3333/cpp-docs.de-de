---
title: Schreiben eines Ausnahmefilters
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 05d3aa79d1293001e80a77b3171b7a4607cd81c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369482"
---
# <a name="writing-an-exception-filter"></a>Schreiben eines Ausnahmefilters

Sie können eine Ausnahme behandeln, indem Sie entweder auf die Ebene des Ausnahmehandlers wechseln oder die Ausführung fortsetzen. Anstatt den Ausnahmehandlercode zu verwenden, um die Ausnahme zu behandeln und durchzufallen, können Sie *Filter* verwenden, um das Problem zu bereinigen und dann durch Zurückgeben von -1 den normalen Fluss fortzusetzen, ohne den Stapel zu löschen.

> [!NOTE]
> Einige Ausnahmen können nicht fortgesetzt werden. Wenn *Filter* für eine solche Ausnahme auf -1 ausgewertet wird, löst das System eine neue Ausnahme aus. Wenn Sie [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)aufrufen, legen Sie fest, ob die Ausnahme fortgesetzt wird.

Der folgende Code verwendet z. B. einen Funktionsaufruf im *Filterausdruck:* Diese Funktion behandelt das Problem und gibt dann -1 zurück, um den normalen Kontrollfluss fortzusetzen:

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

Es ist eine gute Idee, einen Funktionsaufruf im *Filterausdruck* zu verwenden, wenn *Filter* etwas Komplexes tun muss. Das Auswerten des Ausdrucks verursacht die Ausführung der Funktion, in diesem Fall `Eval_Exception`.

Beachten Sie die Verwendung von [GetExceptionCode,](/windows/win32/Debug/getexceptioncode) um die Ausnahme zu bestimmen. Sie müssen diese Funktion innerhalb des Filters selbst aufrufen. `Eval_Exception`kann `GetExceptionCode`nicht aufrufen, aber der Ausnahmecode muss an ihn übergeben werden.

Dieser Handler übergibt die Steuerung an einen anderen Handler, sofern die Ausnahme keine Ganzzahl oder ein Gleitkommaüberlauf ist. Wenn dies der Fall ist, ruft der Handler eine Funktion (`ResetVars` ist nur ein Beispiel, keine API-Funktion) auf, um mehrere globale Variablen zurückzusetzen. *Statement-block-2*, der in diesem Beispiel leer ist, kann nie ausgeführt werden, da `Eval_Exception` nie EXCEPTION_EXECUTE_HANDLER (1) zurückgegeben wird.

Die Verwendung eines Funktionsaufrufs ist ein gutes allgemeines Verfahren für die Behandlung von komplexen Filterausdrücken. Zwei andere hilfreiche Funktionen der Programmiersprache C sind:

- Der bedingte Operator

- Der Kommaoperator

Der bedingte Operator ist häufig nützlich, da er verwendet werden kann, um nach einem bestimmten Rückgabecode zu suchen und dann einen von zwei unterschiedlichen Werten zurückzugeben. Der Filter im folgenden Code erkennt die Ausnahme z. B. nur, wenn die Ausnahme STATUS_INTEGER_OVERFLOW ist:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Der bedingte Operator ist in diesem Fall in erster Linie dafür verantwortlich, Klarheit zu schaffen, da der folgende Code zum gleichen Ergebnis führt:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

Der bedingte Operator ist in Situationen nützlicher, in denen der Filter möglicherweise auf -1 ausgewertet werden soll, EXCEPTION_CONTINUE_EXECUTION.

Der Komma-Operator ermöglicht die Ausführung mehrerer unabhängiger Vorgänge innerhalb eines einzelnen Ausdrucks. Die Wirkung gleicht ungefähr der Ausführung mehrerer Anweisungen und der anschließenden Rückgabe des Wertes des letzten Ausdrucks. Der folgenden Code speichert z. B. den Ausnahmecode in einer Variablen und testet dann auf:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Siehe auch

[Schreiben eines Ausnahmehandlers](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
