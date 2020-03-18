---
title: _execlpe, _wexeclpe
ms.date: 11/04/2016
api_name:
- _execlpe
- _wexeclpe
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wexeclpe
- wexeclpe
- _execlpe
helpviewer_keywords:
- wexeclpe function
- _wexeclpe function
- _execlpe function
- execlpe function
ms.assetid: 07b861da-3e7e-4f1d-bb80-ad69b55e5162
ms.openlocfilehash: 0783e07c945de7d65a11247efc6346c5e315c900
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443025"
---
# <a name="_execlpe-_wexeclpe"></a>_execlpe, _wexeclpe

Lädt neue untergeordnete Prozesse und führt sie aus.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
intptr_t _execlpe(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wexeclpe(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parameter

*cmdname*<br/>
Pfad der auszuführenden Datei.

*arg0*,... *argN*<br/>
Liste von Zeigern zu Parametern.

*envp*<br/>
Array von Zeigern zu Umgebungseinstellungen.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg kehren diese Funktionen nicht zum aufrufenden Prozess zurück. Der Rückgabewert-1 gibt einen Fehler an. in diesem Fall ist die globale Variable **errno** festgelegt.

|**errno** -Wert|BESCHREIBUNG|
|-------------------|-----------------|
|**E2BIG**|Für die Argumente und die Umgebungseinstellungen werden mehr als 32 KB Speicherplatz benötigt.|
|**EACCES**|Für die angegebene Datei ist eine Sperr- oder Freigabeverletzung aufgetreten.|
|**EINVAL**|Ungültiger Parameter.|
|**EMFILE**|Zu viele Dateien geöffnet (die angegebene Datei muss geöffnet werden, damit festgestellt werden kann, ob sie ausführbar ist).|
|**ENOENT**|Die Datei oder der Pfad wurde nicht gefunden.|
|**ENOEXEC**|Die angegebene Datei ist nicht ausführbar oder hat ein ungültiges Format für eine ausführbare Datei.|
|**ENOMEM**|Es ist nicht genügend Arbeitsspeicher, um den neuen Prozess auszuführen; der verfügbare Arbeitsspeicher ist beschädigt; oder es ist ein ungültiger Block vorhanden, was darauf hinweist, dass der aufrufende Prozess nicht ordnungsgemäß zugeordnet wurde.|

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen erstellt einen neuen Prozess und führt diesen aus, übergibt jedes Befehlszeilenargument als separaten Parameter und übergibt außerdem ein Array von Zeigern auf die Umgebungseinstellungen. Diese Funktionen verwenden die **path** -Umgebungsvariable, um die auszuführende Datei zu suchen.

Die **_execlpe** Funktionen überprüfen Ihre Parameter. Wenn entweder *cmdname* oder *arg0* ein NULL-Zeiger oder eine leere Zeichenfolge ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben-1 zurück. Es wird kein neuer Prozess gestartet.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header|Optionaler Header|
|--------------|---------------------|---------------------|
|**_execlpe**|\<process.h>|\<errno.h>|
|**_wexeclpe**|\<process.h> oder \<wchar.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [_exec-, _wexec-Funktionen](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess- und Umgebungssteuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec- und _wexec-Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
