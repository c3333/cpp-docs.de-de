---
title: Schreiben eines Ausnahmefilters
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 5b207e90c1a04a91d85706f6fa4c390ef60c4718
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187296"
---
# <a name="writing-an-exception-filter"></a>Schreiben eines Ausnahmefilters

Sie können eine Ausnahme behandeln, indem Sie entweder auf die Ebene des Ausnahmehandlers wechseln oder die Ausführung fortsetzen. Anstatt den ausnahmehandlercode zur Behandlung der Ausnahme zu verwenden und zu durchlaufen, können Sie *Filter* verwenden, um das Problem zu bereinigen, und dann durch Zurückgeben von-1 den normalen Flow fortsetzen, ohne den Stapel zu löschen.

> [!NOTE]
>  Einige Ausnahmen können nicht fortgesetzt werden. Wenn *Filter* für eine solche Ausnahme zu-1 ausgewertet wird, löst das System eine neue Ausnahme aus. Wenn Sie [raianexception](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)aufzurufen, bestimmen Sie, ob die Ausnahme fortgesetzt wird.

Beispielsweise verwendet der folgende Code einen Funktions aufrufim *Filter* Ausdruck: Diese Funktion behandelt das Problem und gibt dann-1 zurück, um die normale Ablauf Steuerung fortzusetzen:

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

Es empfiehlt sich, einen Funktionsaufruf im *Filter* Ausdruck zu verwenden, wenn der *Filter* einen komplexen Vorgang ausführen muss. Das Auswerten des Ausdrucks verursacht die Ausführung der Funktion, in diesem Fall `Eval_Exception`.

Beachten Sie die Verwendung von [GetExceptionCode](/windows/win32/Debug/getexceptioncode) , um die Ausnahme zu bestimmen. Sie müssen diese Funktion innerhalb des Filters selbst aufrufen. `Eval_Exception` kann `GetExceptionCode`nicht aufzurufen, aber es muss der Ausnahme Code an ihn übermittelt werden.

Dieser Handler übergibt die Steuerung an einen anderen Handler, sofern die Ausnahme keine Ganzzahl oder ein Gleitkommaüberlauf ist. Wenn dies der Fall ist, ruft der Handler eine Funktion (`ResetVars` ist nur ein Beispiel, keine API-Funktion) auf, um mehrere globale Variablen zurückzusetzen. *Statement-Block-2*, das in diesem Beispiel leer ist, kann nie ausgeführt werden, da `Eval_Exception` nie EXCEPTION_EXECUTE_HANDLER (1) zurückgibt.

Die Verwendung eines Funktionsaufrufs ist ein gutes allgemeines Verfahren für die Behandlung von komplexen Filterausdrücken. Zwei andere hilfreiche Funktionen der Programmiersprache C sind:

- Der bedingte Operator

- Der Kommaoperator

Der bedingte Operator ist häufig nützlich, da er verwendet werden kann, um nach einem bestimmten Rückgabecode zu suchen und dann einen von zwei unterschiedlichen Werten zurückzugeben. Beispielsweise erkennt der Filter im folgenden Code die Ausnahme nur, wenn die Ausnahme STATUS_INTEGER_OVERFLOW ist:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Der bedingte Operator ist in diesem Fall in erster Linie dafür verantwortlich, Klarheit zu schaffen, da der folgende Code zum gleichen Ergebnis führt:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

Der bedingte Operator ist nützlicher in Situationen, in denen Sie den Filter möglicherweise als-1, EXCEPTION_CONTINUE_EXECUTION auswerten möchten.

Der Komma-Operator ermöglicht die Ausführung mehrerer unabhängiger Vorgänge innerhalb eines einzelnen Ausdrucks. Die Wirkung gleicht ungefähr der Ausführung mehrerer Anweisungen und der anschließenden Rückgabe des Wertes des letzten Ausdrucks. Der folgenden Code speichert z. B. den Ausnahmecode in einer Variablen und testet dann auf:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Ausnahme Handlers](../cpp/writing-an-exception-handler.md)<br/>
[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
