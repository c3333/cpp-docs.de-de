---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348151"
---
# <a name="_cwait"></a>_cwait

Wartet, bis ein anderer Prozess beendet wird.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>Parameter

*termstat*<br/>
Zeiger auf einen Puffer, in dem der Ergebniscode des angegebenen Prozesses gespeichert wird, oder **NULL**.

*procHandle*<br/>
Das Handle für den Prozess, auf den gewartet werden soll (d. h. der Prozess, der beendet werden muss, bevor **_cwait** zurückkehren kann).

*action*<br/>
NULL: Von Windows-Betriebssystemanwendungen ignoriert; für andere Anwendungen: Aktionscode für *procHandle*.

## <a name="return-value"></a>Rückgabewert

Wenn der angegebene Prozess erfolgreich abgeschlossen wurde, gibt das Handle des angegebenen Prozesses zurück und legt *termstat* auf den Ergebniscode fest, der vom angegebenen Prozess zurückgegeben wird. Andernfalls gibt -1 zurück und setzt **errno** wie folgt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|**ECHILD**|Es ist kein angegebener Prozess vorhanden, *procHandle* ist ungültig, oder der Aufruf der [GetExitCodeProcess-](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) oder [WaitForSingleObject-API](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) ist fehlgeschlagen.|
|**Einval**|*Aktion* ist ungültig.|

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_cwait-Funktion** wartet auf die Beendigung der Prozess-ID des angegebenen Prozesses, der von *procHandle*bereitgestellt wird. Der Wert von *procHandle,* der an **_cwait** übergeben wird, sollte der Wert sein, der vom Aufruf an die [_spawn-Funktion](../../c-runtime-library/spawn-wspawn-functions.md) zurückgegeben wird, die den angegebenen Prozess erstellt hat. Wenn die Prozess-ID beendet wird, bevor **_cwait** aufgerufen wird, **wird _cwait** sofort zurückgegeben. **_cwait** kann von jedem Prozess verwendet werden, um auf einen anderen bekannten Prozess zu warten, für den ein gültiges Handle (*procHandle*) vorhanden ist.

*termstat* verweist auf einen Puffer, in dem der Rückgabecode des angegebenen Prozesses gespeichert wird. Der Wert von *termstat* gibt an, ob der angegebene Prozess normalerweise durch Aufrufen der Windows [ExitProcess-API](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) beendet wurde. **ExitProcess** wird intern aufgerufen, wenn der angegebene Prozess **Exit** oder **_exit**aufruft, vom **Main**zurückkehrt oder das Ende von **main**erreicht. Weitere Informationen zu dem Wert, der über *termstat*zurückübergaben, finden Sie unter [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Wenn **_cwait** aufgerufen wird, indem ein **NULL-Wert** für *termstat*verwendet wird, wird der Rückgabecode des angegebenen Prozesses nicht gespeichert.

Der *Aktionsparameter* wird vom Windows-Betriebssystem ignoriert, da Eltern-Kind-Beziehungen in diesen Umgebungen nicht implementiert sind.

Sofern *procHandle* nicht -1 oder -2 ist (Handles für den aktuellen Prozess oder Thread), wird das Handle geschlossen. Daher sollte in dieser Situation das zurückgegebene Handle nicht verwendet werden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
