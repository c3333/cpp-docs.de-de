---
title: _chdrive
ms.date: 4/2/2020
api_name:
- _chdrive
- _o__chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 0c19fefcf6a766842ee2e25cbe6bdb61bbf48e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333343"
---
# <a name="_chdrive"></a>_chdrive

Ändert das aktuelle Laufwerk.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parameter

*Laufwerk*<br/>
Eine ganze Zahl von 1 bis 26, die das aktuelle Laufwerk angibt (1=A, 2=B usw.).

## <a name="return-value"></a>Rückgabewert

Null (0), wenn das aktuelle Laufwerk erfolgreich geändert wurde; andernfalls – 1.

## <a name="remarks"></a>Bemerkungen

Wenn sich das *Laufwerk* nicht im Bereich von 1 bis 26 befindet, wird der invalid-parameter-Handler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben aufgerufen. Wenn die Ausführung fortgesetzt werden darf, gibt die **_chdrive-Funktion** -1 zurück, **errno** wird auf **EACCES**und **_doserrno** auf **ERROR_INVALID_DRIVE**festgelegt.

Die Funktion **_chdrive** ist nicht threadsicher, da sie von der Funktion **SetCurrentDirectory** abhängt, die selbst nicht threadsicher ist. Um **_chdrive** sicher in einer Multithreadanwendung zu verwenden, müssen Sie eine eigene Threadsynchronisierung bereitstellen. Weitere Informationen finden Sie unter [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

Die Funktion **_chdrive** ändert nur das aktuelle Arbeitslaufwerk; **_chdir** ändert das aktuelle Arbeitsverzeichnis.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Beachten Sie das Beispiel für [_getdrive](getdrive.md).

## <a name="see-also"></a>Siehe auch

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
