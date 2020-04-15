---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: c3f1b9bd8bf2a4404e2239858e4c3c59b755bacd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332376"
---
# <a name="_set_new_handler"></a>_set_new_handler

Übergibt die Steuerung an den Fehlerbehandlungsmechanismus, wenn der **new**-Operator keine Speicherbelegung vornehmen kann.

## <a name="syntax"></a>Syntax

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parameter

*pNewHandler*<br/>
Zeiger zu der von der Anwendung bereitgestellten Speicherbehandlungsfunktion. Ist das Argument 0, wird der neue Ereignishandler entfernt.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die vorherige Ausnahmebehandlungsfunktion zurück, die von **_set_new_handler**registriert wurde, sodass die vorherige Funktion später wiederhergestellt werden kann. Wenn keine vorherige Funktion festgelegt wurde, kann der Rückgabewert verwendet werden, um das Standardverhalten wiederherzustellen. Dieser Wert kann **NULL**sein.

## <a name="remarks"></a>Bemerkungen

Die C++-_set_new_handler-Funktion gibt eine Ausnahmebehandlungsfunktion an, die die Kontrolle erhält, wenn der **neue** Operator keinen Speicher zuweist. **_set_new_handler** Wenn **neu** fehlschlägt, ruft das Laufzeitsystem automatisch die Ausnahmebehandlungsfunktion auf, die als Argument an **_set_new_handler**übergeben wurde. **_PNH**, die in New.h definiert ist, ist ein Zeiger auf eine Funktion, die den Typ **int** zurückgibt und ein Argument vom Typ **size_t**annimmt. Verwenden Sie **size_t,** um den zuzuweisenden Speicherplatz anzugeben.

Es ist kein Standardhandler vorhanden.

**_set_new_handler** ist im Wesentlichen ein Garbage Collection-Schema. Das Laufzeitsystem wiederholt die Zuordnung jedes Mal, wenn die Funktion einen Wert ungleich null zurückgibt, und schlägt fehl, wenn die Funktion 0 zurückgibt.

Ein Vorkommen der **_set_new_handler-Funktion** in einem Programm registriert die in der Argumentliste angegebene Ausnahmebehandlungsfunktion beim Laufzeitsystem:

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

Sie können die Funktionsadresse, die zuletzt an die **_set_new_handler-Funktion** übergeben wurde, speichern und später wieder setzen:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

Die C++-Funktion [_set_new_mode](set-new-mode.md) legt den neuen Handlermodus für [malloc](malloc.md) fest. Der neue Handlermodus gibt an, ob **malloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie von **_set_new_handler**festgelegt. Standardmäßig ruft **malloc** die neue Handlerroutine bei Nichtzuweisung von Arbeitsspeicher nicht auf. Sie können dieses Standardverhalten überschreiben, sodass **malloc** die neue Handlerroutine auf die gleiche Weise aufruft, wenn **malloc** keinen Speicher zuweist, wie der **neue** Operator dies tut, wenn er aus demselben Grund fehlschlägt. Um den Standardwert zu überschreiben, rufen Sie

```cpp
_set_new_mode(1);
```

rechtzeitig im Programm auf, oder stellen Sie eine Verknüpfung mit Newmode.obj her.

Wenn eine benutzerdefinierte `operator new` bereitgestellt wird, werden die neuen Handlerfunktionen bei Einem Fehler nicht automatisch aufgerufen.

Weitere Informationen finden Sie unter [new](../../cpp/new-operator-cpp.md) und [delete](../../cpp/delete-operator-cpp.md) in der *C++-Sprachreferenz*.

Es gibt einen einzelnen **_set_new_handler-Handler** für alle dynamisch verknüpften DLLs oder ausführbaren Dateien. Auch wenn Sie **_set_new_handler** wird der Handler möglicherweise durch einen anderen ersetzt oder dass Sie einen Handler ersetzen, der durch eine andere DLL oder ausführbare Datei festgelegt wurde.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Wenn – wie in diesem Beispiel – die Zuordnung fehlschlägt, wird die Steuerung an MyNewHandler übergeben. Das an MyNewHandler übergebene Argument ist die Anzahl der angeforderten Bytes. Der von MyNewHandler zurückgegebene Wert ist ein Flag, das angibt, ob die Zuordnung wiederholt werden soll: Ein Wert ungleich null gibt an, dass die Zuordnung wiederholt werden soll, und der Wert 0 gibt an, dass die Verteilung fehlgeschlagen ist.

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[kostenlos](free.md)<br/>
[realloc](realloc.md)<br/>
