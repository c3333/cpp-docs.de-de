---
title: _spawnlpe, _wspawnlpe
ms.date: 11/04/2016
api_name:
- _spawnlpe
- _wspawnlpe
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
- _wspawnlpe
- _spawnlpe
- wspawnlpe
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
ms.openlocfilehash: 4fd7275969120b35253bbc12098f8dc8f69a1fed
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442499"
---
# <a name="_spawnlpe-_wspawnlpe"></a>_spawnlpe, _wspawnlpe

Erstellt einen neuen Prozess und führt ihn aus.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
intptr_t _spawnlpe(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnlpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parameter

*mode*<br/>
Ausführungsmodus für den aufrufenden Prozess.

*cmdname*<br/>
Pfad der auszuführenden Datei.

*arg0*, *arg1*,... *argN*<br/>
Liste von Zeigern zu Argumenten. Das *arg0* -Argument ist normalerweise ein Zeiger auf *cmdname*. Die Argumente *arg1* über *argN* sind Zeiger auf die Zeichen folgen, die die neue Argumentliste bilden. Nach *argN*muss ein **null** -Zeiger vorhanden sein, um das Ende der Argumentliste zu markieren.

*envp*<br/>
Array von Zeigern zu Umgebungseinstellungen.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert eines synchronen **_spawnlpe** oder **_wspawnlpe** ( **_P_WAIT** für den- *Modus*angegeben) ist der Beendigungs Status des neuen Prozesses. Der Rückgabewert eines asynchronen **_spawnlpe** oder **_wspawnlpe** ( **_P_NOWAIT** oder **_P_NOWAITO** , der für den- *Modus*angegeben ist) ist das Prozess handle. Der Beendigungsstatus ist 0, wenn der Prozess ordnungsgemäß beendet wurde. Sie können den Beendigungs Status auf einen Wert ungleich 0 (null) festlegen, wenn der erzeugte Prozess speziell ein Argument ungleich Null zum Aufrufen der Beendigungs **Routine verwendet** . Wenn der neue Prozess nicht explizit einen positiven Beendigungsstatus eingestellt hat, weist ein positiver Beendigungsstatus auf eine abnormale Beendigung aufgrund eines Abbruchs oder einer Unterbrechung hin. Der Rückgabewert-1 gibt einen Fehler an (der neue Prozess wird nicht gestartet). In diesem Fall wird **errno** auf einen der folgenden Werte festgelegt.

|||
|-|-|
| **E2BIG** | Argumentliste umfasst mehr als 1024 Byte. |
| **EINVAL** | Das *Mode* -Argument ist ungültig. |
| **ENOENT** | Datei oder Pfad nicht gefunden. |
| **ENOEXEC** | Die angegebene Datei ist nicht ausführbar oder hat ein ungültiges Format für eine ausführbare Datei. |
| **ENOMEM** | Es ist nicht genügend Arbeitsspeicher verfügbar, um den neuen Prozess auszuführen. |

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen erstellt einen neuen Prozess und führt diesen aus, übergibt jedes Befehlszeilenargument als separaten Parameter und übergibt außerdem ein Array von Zeigern auf die Umgebungseinstellungen. Diese Funktionen verwenden die **path** -Umgebungsvariable, um die auszuführende Datei zu suchen.

Diese Funktionen überprüfen ihre Parameter. Wenn entweder *cmdname* oder *arg0* eine leere Zeichenfolge oder ein NULL-Zeiger ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL**fest und geben-1 zurück. Es wird kein neuer Prozess erzeugt.

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_spawnlpe**|\<process.h>|
|**_wspawnlpe**|\<stdio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess- und Umgebungssteuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec- und _wexec-Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
