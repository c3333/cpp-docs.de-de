---
title: _cwait
description: API-Referenz für die Microsoft Visual C-Lauf Zeit `_cwait()` Funktion.
ms.date: 10/23/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5b4c4db3c40645b947583b722d345c2e80dcaa8e
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639106"
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

*`termstat`*\
Zeiger auf einen Puffer, in dem der Ergebniscode des angegebenen Prozesses gespeichert wird, oder **`NULL`** .

*`procHandle`*\
Das Handle für den Prozess, auf den gewartet werden soll (d. h. der Prozess, der beendet werden muss, bevor **_cwait** zurückgeben kann).

*`action`*\
**`NULL`** : Wird von Anwendungen des Windows-Betriebssystems ignoriert. für andere Anwendungen: Aktions Code, der für ausgeführt werden soll *`procHandle`* .

## <a name="return-value"></a>Rückgabewert

Wenn der angegebene Prozess erfolgreich abgeschlossen wurde, wird das Handle des angegebenen Prozesses zurückgegeben und *`termstat`* auf den Ergebniscode festgelegt, der vom angegebenen Prozess zurückgegeben wird. Andernfalls wird-1 zurückgegeben und **`errno`** wie folgt festgelegt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|**`ECHILD`**|Es ist kein angegebener Prozess vorhanden, *`procHandle`* ist ungültig, oder der Rückruf der- [`GetExitCodeProcess`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) oder-API ist [`WaitForSingleObject`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) fehlgeschlagen.|
|**`EINVAL`**|*`action`* ist ungültig.|

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Hinweise

Die **`_cwait`** -Funktion wartet auf die Beendigung der Prozess-ID des angegebenen Prozesses, der von bereitgestellt wird *`procHandle`* . Der Wert von *`procHandle`* , der an übermittelt **`_cwait`** wird, sollte der Wert sein, der durch den-Rückruf der Funktion zurückgegeben wird [`_spawn`](../../c-runtime-library/spawn-wspawn-functions.md) , die den angegebenen Prozess erstellt hat. Wenn die Prozess-ID vor dem Aufruf von beendet **`_cwait`** wird, wird **`_cwait`** sofort zurückgegeben. **`_cwait`** kann von jedem Prozess verwendet werden, um auf einen anderen bekannten Prozess zu warten, für den ein gültiges Handle ( *`procHandle`* ) vorhanden ist.

*`termstat`* verweist auf einen Puffer, in dem der Rückgabecode des angegebenen Prozesses gespeichert wird. Der Wert von *`termstat`* gibt an, ob der angegebene Prozess durch Aufrufen der Windows-API ordnungsgemäß beendet wurde [`ExitProcess`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) . **`ExitProcess`** wird intern aufgerufen, wenn der angegebene Prozess **`exit`** oder aufruft **`_exit`** , von zurückkehrt **`main`** oder das Ende von erreicht **`main`** . Weitere Informationen zu dem Wert, der zurückgegeben *`termstat`* wird, finden Sie [unter GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Wenn **`_cwait`** mit einem **`NULL`** Wert für aufgerufen wird *`termstat`* , wird der Rückgabecode des angegebenen Prozesses nicht gespeichert.

Der *`action`* -Parameter wird vom Windows-Betriebssystem ignoriert, da Beziehungen zwischen übergeordneten und untergeordneten Elementen in diesen Umgebungen nicht implementiert werden.

Sofern nicht *`procHandle`* -1 oder-2 ist (Handles für den aktuellen Prozess oder Thread), wird das Handle geschlossen. Verwenden Sie in dieser Situation das zurückgegebene Handle nicht.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**`_cwait`**|\<process.h>|\<errno.h>|

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
    intptr_t hProcess;
    char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main(int argc, char* argv[])
{
    int termstat, c;
    unsigned int number;

    srand((unsigned)time(NULL));    // Seed randomizer

    // If no arguments, this is the calling process
    if (argc == 1)
    {
        // Spawn processes in numeric order
        for (c = 0; c < 4; c++) {
            _flushall();
            process[c].hProcess = _spawnl(_P_NOWAIT, argv[0], argv[0],
                process[c].name, NULL);
        }

        // Wait for randomly specified process, and respond when done
        c = getrandom(0, 3);
        printf("Come here, %s.\n", process[c].name);
        _cwait(&termstat, process[c].hProcess, _WAIT_CHILD);
        printf("Thank you, %s.\n", process[c].name);

    }
    // If there are arguments, this must be a spawned process
    else
    {
        // Delay for a period that's determined by process number
        Sleep((argv[1][0] - 'A' + 1) * 1000L);
        printf("Hi, Dad. It's %s.\n", argv[1]);
    }
}
```

Die Reihenfolge der Ausgabe variiert je nach Testlauf.

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)\
[_spawn, _wspawn Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)
