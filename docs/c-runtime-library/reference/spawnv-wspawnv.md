---
title: _spawnv, _wspawnv
ms.date: 4/2/2020
api_name:
- _wspawnv
- _spawnv
- _o__spawnv
- _o__wspawnv
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
- wspawnv
- _spawnv
- _wspawnv
helpviewer_keywords:
- wspawnv function
- processes, creating
- _spawnv function
- processes, executing new
- process creation
- _wspawnv function
- spawnv function
ms.assetid: 72360ef4-dfa9-44c1-88c1-b3ecb660aa7d
ms.openlocfilehash: f4a4d695e265c28efd1b9da8588752d8b2635163
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355892"
---
# <a name="_spawnv-_wspawnv"></a>_spawnv, _wspawnv

Erstellt einen neuen Prozess und führt ihn aus.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
intptr_t _spawnv(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnv(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parameter

*Modus*<br/>
Ausführungsmodus für den aufrufenden Prozess.

*cmdname*<br/>
Pfad der auszuführenden Datei.

*Argv*<br/>
Array von Zeigern zu Argumenten. Das Argument *argv*[0] ist in der Regel ein Zeiger auf einen Pfad im realen Modus oder auf den Programmnamen im geschützten Modus, und *argv*[1] durch *argv*[**n**] sind Zeiger auf die Zeichenfolgen, die die neue Argumentliste bilden. Das Argument *argv*[**n** +1] muss ein **NULL-Zeiger** sein, um das Ende der Argumentliste zu markieren.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert aus einem synchronen **_spawnv** oder **_wspawnv** (**_P_WAIT** für *Modus*angegeben) ist der Exit-Status des neuen Prozesses. Der Rückgabewert aus einem asynchronen **_spawnv** oder **_wspawnv** **(_P_NOWAIT** oder **_P_NOWAITO** für *Modus*angegeben) ist das Prozesshandle. Der Beendigungsstatus ist 0, wenn der Prozess ordnungsgemäß beendet wurde. Sie können den Exit-Status auf einen Wert ungleich Null festlegen, wenn der erstellte Prozess die **Exit-Routine** mit einem Argument ungleich Null aufruft. Wenn der neue Prozess nicht explizit einen positiven Beendigungsstatus eingestellt hat, weist ein positiver Beendigungsstatus auf eine abnormale Beendigung mit einem Abbruch oder einer Unterbrechung hin. Ein Rückgabewert von -1 gibt einen Fehler an (der neue Prozess wird nicht gestartet). In diesem Fall wird **errno** auf einen der folgenden Werte gesetzt.

|||
|-|-|
| **E2BIG** | Argumentliste umfasst mehr als 1024 Byte. |
| **Einval** | *Modusargument* ist ungültig. |
| **ENOENT** | Datei oder Pfad nicht gefunden. |
| **ENOEXEC** | Die angegebene Datei ist nicht ausführbar oder hat ein ungültiges Format für eine ausführbare Datei. |
| **Enomem** | Es ist nicht genügend Arbeitsspeicher verfügbar, um den neuen Prozess auszuführen. |

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen erstellt einen neuen Prozess, führt ihn aus und übergibt ein Array von Zeigern auf Befehlszeilenargumente.

Diese Funktionen überprüfen ihre Parameter. Wenn *entweder cmdname* oder *argv* ein Nullzeiger ist oder *wenn argv* auf null Zeiger oder *argv*[0] eine leere Zeichenfolge ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, legen diese Funktionen **errno** auf **EINVAL**fest und geben -1 zurück. Es wird kein neuer Prozess erzeugt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_spawnv**|\<stdio.h> oder \<process.h>|
|**_wspawnv**|\<stdio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[Abbrechen](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
