---
title: _resetstkoflw
ms.date: 4/2/2020
api_name:
- _resetstkoflw
- _o__resetstkoflw
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: b19b66279427aa4623cff037e67067096eb6bd42
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917783"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

Führt nach einem Stapelüberlauf eine Wiederherstellung durch.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Funktion ist der Wert ungleich 0 (null), sonst Null.

## <a name="remarks"></a>Hinweise

Die **_resetstkoflw** -Funktion stellt eine Stapelüberlauf Bedingung wieder her, sodass ein Programm fortgesetzt werden kann, anstatt einen schwerwiegenden Ausnahme Fehler zu verursachen. Wenn die **_resetstkoflw** -Funktion nicht aufgerufen wird, gibt es nach der vorherigen Ausnahme keine Schutz Seiten. Beim nächsten Stapelüberlauf treten keine Ausnahmen auf, und der Prozess wird ohne Ausgabe einer Warnung beendet.

Wenn ein Thread in einer Anwendung eine **EXCEPTION_STACK_OVERFLOW**-Ausnahme verursacht, hat der Thread seinen Stapel in einem beschädigten Zustand belassen. Dies steht im Gegensatz zu anderen Ausnahmen wie **EXCEPTION_ACCESS_VIOLATION** oder **EXCEPTION_INT_DIVIDE_BY_ZERO**, bei denen der Stapel nicht beschädigt ist. Der Stapel ist auf einen beliebig kleinen Wert festgelegt, wenn das Programm das erste Mal geladen wird. Der Stapel vergrößert sich dann bei Bedarf, um die Anforderungen des Threads zu erfüllen. Dieses wird implementiert, indem eine Seite mit PAGE_GUARD-Zugriff am Ende des aktuellen Stapel eingefügt wird. Weitere Informationen finden Sie unter dem Link zum [Erstellen von Schutzseiten](/windows/win32/Memory/creating-guard-pages).

Wenn der Code den Stapelzeiger veranlasst, auf eine Adresse auf dieser Seite zu zeigen, wird eine Ausnahme ausgelöst und das System führt die folgenden drei Schritte durch:

- Entfernen des PAGE_GUARD-Schutzes auf der Schutzseite, sodass der Thread Daten im Speicher lesen und schreiben kann.

- Zuordnen einer neuen Schutzseite, die sich eine Seite unterhalb der letzten befindet.

- Wiederholen der Anweisung, die die Ausnahme ausgelöst hat.

Auf diese Weise kann das System die Größe des Stapels für den Thread automatisch erhöhen. Jeder Thread in einem Prozess hat eine maximale Stapelgröße. Die Stapelgröße wird zur Kompilierungszeit durch die [/STACK (Stapelreservierung)](../../build/reference/stack-stack-allocations.md)- oder die [STACKSIZE](../../build/reference/stacksize.md)-Anweisung in der DEF-Datei des Projekts festgelegt.

Wenn die maximale Stapelgröße überschritten wird, führt das System die folgenden drei Schritte aus:

- Entfernen des PAGE_GUARD-Schutzes auf der Schutzseite, wie zuvor beschrieben.

- Versuchen, eine neue Schutzseite unterhalb des letzten zuzuweisen. Dies schlägt jedoch fehl, da die maximale Stapelgröße überschritten wurde.

- Auslösen einer Ausnahme, sodass der Thread diese im Ausnahmeblock behandeln kann.

Beachten Sie, dass der Stapel ab diesem Punkt keine Schutzseite mehr hat. Wenn das Programm das nächste Mal den Stapel bis zu dem Ende vergrößert, an dem eine Schutzseite vorhanden sein sollte, schreibt das Programm über den Stapel hinaus und verursacht eine Zugriffsverletzung.

Wenden Sie **_resetstkoflw** an, um die Schutz Seite wiederherzustellen, wenn die Wiederherstellung nach einer Stapelüberlauf Ausnahme erfolgt. Diese Funktion kann innerhalb des Haupt Texts eines **__except** Blocks oder außerhalb eines **__except** Blocks aufgerufen werden. Es gibt jedoch einige Einschränkungen hinsichtlich der Verwendung. **_resetstkoflw** sollten nie aufgerufen werden von:

- einem Filterausdruck

- einer Filterfunktion

- einer Funktion, die von einer Filterfunktion aufgerufen wurde.

- Ein **catch**-Block.

- Ein **__finally** -Block.

An diesen Punkten ist der Stapel noch nicht ausreichend entladen.

Stapelüberlauf-Ausnahmen werden als strukturierte Ausnahmen und nicht als C++-Ausnahmen generiert, sodass **_resetstkoflw** in einem normalen **catch** -Block nicht hilfreich ist, da eine Stapelüberlauf Ausnahme nicht abgefangen wird. Wenn allerdings [_set_se_translator](set-se-translator.md) verwendet wird, um einen strukturierten Ausnahmeübersetzer zu implementieren, der C++-Ausnahmen auslöst (siehe zweites Beispiel), führt eine Stapelüberlauf-Ausnahme zu einer C++-Ausnahme, die von einem C++-Catch-Block behandelt werden kann.

Das Aufrufen von **_resetstkoflw** in einem C++-Catch-Block, der von einer Ausnahme erreicht wird, die von einer strukturierten Ausnahmeübersetzerfunktion ausgelöst wird, ist nicht sicher. In diesem Fall wird der Stapelspeicher nicht freigegeben und die Stapelzeiger wird nicht bis außerhalb des Catch-Blocks zurückgesetzt, auch wenn Destruktoren für alle zerstörbaren Objekte vor dem Catch-Block aufgerufen wurden. Diese Funktion sollte erst aufgerufen werden, wenn der Stapelspeicher freigegeben und der Stapelzeiger zurückgesetzt wurde. Daher sollte sie erst nach dem Beenden des Catch-Blocks aufgerufen werden. Im Catch-Block sollte so wenig Stapelspeicherplatz verwendet werden wie möglich, da ein Stapelüberlauf, der in einem Catch-Block auftritt, der selbst versucht, sich nach einem vorherigen Stapelüberlauf wiederherzustellen, nicht wiederhergestellt werden kann und dazu führen kann, dass das Programm nicht mehr reagiert, da der Überlauf in dem Catch-Block eine Ausnahme auslöst, die vom selben Catch-Block behandelt wird.

Es gibt Situationen, in denen **_resetstkoflw** trotz Verwendung am richtigen Speicherort fehlschlagen kann, beispielsweise in einem **__except**-Block. Wenn selbst nach der Stapelentladung nicht genug Stapelspeicher vorhanden ist, um **_resetstkoflw** ausführen, ohne auf die letzte Seite des Stapels zu schreiben, dann schlägt **_resetstkoflw** fehl, kann die letzte Seite des Stapels nicht als Schutzseite wiederherstellen und gibt 0 zurück, um einen Fehler anzuzeigen. Daher sollte zu einer sicheren Verwendung dieser Funktion das Überprüfen des Rückgabewerts gehören, anstatt davon auszugehen, dass der Stapel sicher verwendet werden kann.

Die strukturierte Ausnahmebehandlung fängt keine **STATUS_STACK_OVERFLOW** Ausnahme ab, wenn die Anwendung mit **/CLR** kompiliert wird (siehe [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md)).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliotheken:** Alle Versionen der [CRT-Bibliotheksfunktionen](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die empfohlene Verwendung der **_resetstkoflw** -Funktion.

```C
// crt_resetstkoflw.c
// Launch program with and without arguments to observe
// the difference made by calling _resetstkoflw.

#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void recursive(int recurse)
{
   _alloca(2000);
   if (recurse)
      recursive(recurse);
}

// Filter for the stack overflow exception.
// This function traps the stack overflow exception, but passes
// all other exceptions through.
int stack_overflow_exception_filter(int exception_code)
{
   if (exception_code == EXCEPTION_STACK_OVERFLOW)
   {
       // Do not call _resetstkoflw here, because
       // at this point, the stack is not yet unwound.
       // Instead, signal that the handler (the __except block)
       // is to be executed.
       return EXCEPTION_EXECUTE_HANDLER;
   }
   else
       return EXCEPTION_CONTINUE_SEARCH;
}

int main(int ac)
{
   int i = 0;
   int recurse = 1, result = 0;

   for (i = 0 ; i < 10 ; i++)
   {
      printf("loop #%d\n", i + 1);
      __try
      {
         recursive(recurse);

      }

      __except(stack_overflow_exception_filter(GetExceptionCode()))
      {
         // Here, it is safe to reset the stack.

         if (ac >= 2)
         {
            puts("resetting stack overflow");
            result = _resetstkoflw();
         }
      }

      // Terminate if _resetstkoflw failed (returned 0)
      if (!result)
         return 3;
   }

   return 0;
}
```

Beispielausgabe ohne Programm Argumente:

```Output
loop #1
```

Das Programm reagiert nicht mehr, ohne weitere Iterationen auszuführen.

Mit Programmargumenten:

```Output
loop #1
resetting stack overflow
loop #2
resetting stack overflow
loop #3
resetting stack overflow
loop #4
resetting stack overflow
loop #5
resetting stack overflow
loop #6
resetting stack overflow
loop #7
resetting stack overflow
loop #8
resetting stack overflow
loop #9
resetting stack overflow
loop #10
resetting stack overflow
```

### <a name="description"></a>Beschreibung

Das folgende Beispiel zeigt die empfohlene Verwendung von **_resetstkoflw** in einem Programm, in dem strukturierte Ausnahmen in C++-Ausnahmen konvertiert werden.

### <a name="code"></a>Code

```cpp
// crt_resetstkoflw2.cpp
// compile with: /EHa
// _set_se_translator requires the use of /EHa
#include <malloc.h>
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class Exception { };

class StackOverflowException : Exception { };

// Because the overflow is deliberate, disable the warning that
// this function will cause a stack overflow.
#pragma warning (disable: 4717)
void CauseStackOverflow (int i)
{
    // Overflow the stack by allocating a large stack-based array
    // in a recursive function.
    int a[10000];
    printf("%d ", i);
    CauseStackOverflow (i + 1);
}

void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)
{
    // For stack overflow exceptions, throw our own C++
    // exception object.
    // For all other exceptions, throw a generic exception object.
    // Use minimal stack space in this function.
    // Do not call _resetstkoflw in this function.

    if (code == EXCEPTION_STACK_OVERFLOW)
        throw StackOverflowException ( );
    else
        throw Exception( );
}

int main ( )
{
    bool stack_reset = false;
    bool result = false;

    // Set up a function to handle all structured exceptions,
    // including stack overflow exceptions.
    _set_se_translator (SEHTranslator);

    try
    {
        CauseStackOverflow (0);
    }
    catch (StackOverflowException except)
    {
        // Use minimal stack space here.
        // Do not call _resetstkoflw here.
        printf("\nStack overflow!\n");
        stack_reset = true;
    }
    catch (Exception except)
    {
        // Do not call _resetstkoflw here.
        printf("\nUnknown Exception!\n");
    }
    if (stack_reset)
    {
        result = _resetstkoflw();
        // If stack reset failed, terminate the application.
        if (result == 0)
            exit(1);
    }

    void* pv = _alloca(100000);
    printf("Recovered from stack overflow and allocated 100,000 bytes"
           " using _alloca.");

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>Weitere Informationen

[_alloca](alloca.md)<br/>
