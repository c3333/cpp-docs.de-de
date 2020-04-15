---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345031"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Holt das Betriebssystem-Dateihandle, das dem angegebenen Dateideskriptor zugeordnet ist.

## <a name="syntax"></a>Syntax

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Eine vorhandener Dateideskriptor.

## <a name="return-value"></a>Rückgabewert

Gibt ein Betriebssystemdateihandle zurück, wenn *fd* gültig ist. Ansonsten wird der ungültige Parameterhandler, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben, aufgerufen. Wenn die Ausführung fortgesetzt werden darf, wird **INVALID_HANDLE_VALUE** (-1) zurückgegeben. Außerdem wird **errno** auf **EBADF**festgelegt, was auf ein ungültiges Dateihandle hinweist. Um eine Warnung zu vermeiden, wenn das Ergebnis als Win32-Dateihandle verwendet wird, geben Sie es in einen **HANDLE-Typ** um.

> [!NOTE]
> Wenn **stdin**, **stdout**und **stderr** nicht mit einem Stream verknüpft sind (z. B. in einer Windows-Anwendung ohne Konsolenfenster), werden die Dateideskriptorwerte für diese Streams von [_fileno](fileno.md) als Sonderwert -2 zurückgegeben. Wenn Sie anstelle eines Aufrufs von **_fileno**einen Parameter 0, 1 oder 2 als Dateideskriptor verwenden, **gibt _get_osfhandle** auch den speziellen Wert -2 zurück, wenn der Dateideskriptor keinem Stream zugeordnet ist, und legt **errno**nicht fest. Dies ist jedoch kein gültiger Dateihandlewert, und nachfolgende Aufrufe, die versuchen, ihn zu verwenden, werden wahrscheinlich fehlschlagen.

Weitere Informationen **zu EBADF** und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Um eine Datei zu schließen, deren Betriebssystemdateihandle von **_get_osfhandle**abgerufen wird, rufen Sie [_close](close.md) auf dem Dateideskriptor *fd*auf. Rufen Sie **CloseHandle** niemals für den Rückgabewert dieser Funktion auf. Das zugrunde liegende OS-Dateihandle befindet sich im Besitz des [_close](close.md) fd-Dateideskriptors und wird geschlossen, wenn _close auf *fd*aufgerufen wird. *fd* Wenn der Dateideskriptor im `FILE *` Besitz eines Streams ist, schließt der Aufruf von [fclose](fclose-fcloseall.md) für diesen `FILE *` Stream sowohl den Dateideskriptor als auch das zugrunde liegende OS-Dateihandle. Rufen Sie in diesem Fall [keine _close](close.md) für den Dateideskriptor auf.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
