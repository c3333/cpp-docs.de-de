---
title: system, _wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 21ce04d30da80a40a1162dce06ff378150008766
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362791"
---
# <a name="system-_wsystem"></a>system, _wsystem

Führt einen Befehl aus.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>Parameter

*Befehl*<br/>
Der Befehl, der ausgeführt werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn *der Befehl* **NULL** ist und der Befehlsinterpreter gefunden wird, gibt er einen Wert ungleich Null zurück. Wenn der Befehlsinterpreter nicht gefunden wird, gibt 0 zurück und setzt **errno** auf **ENOENT**. Wenn *der Befehl* nicht **NULL**ist, gibt **system** den Wert zurück, der vom Befehlsinterpreter zurückgegeben wird. Gibt den Wert 0 nur zurück, wenn der Befehlsinterpreter den Wert 0 zurückgibt. Ein Rückgabewert von - 1 gibt einen Fehler an, und **errno** wird auf einen der folgenden Werte gesetzt:

|||
|-|-|
| **E2BIG** | Die Argumentliste (systemabhängig) ist zu groß. |
| **ENOENT** | Der Befehlsinterpreter kann nicht gefunden werden. |
| **ENOEXEC** | Die Befehlsinterpreterdatei kann nicht ausgeführt werden, da das Format ungültig ist. |
| **Enomem** | Es ist nicht genügend Arbeitsspeicher verfügbar, um den Befehl auszuführen; der verfügbare Arbeitsspeicher ist beschädigt; oder es ist ein ungültiger Block vorhanden, was darauf hinweist, dass der aufrufende Prozess nicht ordnungsgemäß zugeordnet wurde. |

Weitere Informationen zu diesen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **Systemfunktion** übergibt den *Befehl* an den Befehlsinterpreter, der die Zeichenfolge als Betriebssystembefehl ausführt. **system** verwendet die Umgebungsvariablen **COMSPEC** und **PATH,** um die Befehlsinterpreterdatei CMD.exe zu finden. Wenn *der Befehl* **NULL**ist, prüft die Funktion nur, ob der Befehlsinterpreter vorhanden ist.

Sie müssen den Stream explizit leeren, indem Sie [fflush](fflush.md) oder [_flushall](flushall.md)verwenden, oder einen beliebigen Stream schließen, bevor Sie **system**aufrufen.

**_wsystem** ist eine breitgefächerte Version des **Systems;** Das *Befehlsargument* für **_wsystem** ist eine Zeichenfolge mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**System**|**System**|**_wsystem**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**System**|\<process.h> oder \<stdlib.h>|
|**_wsystem**|\<process.h> oder \<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

In diesem Beispiel wird **system** verwendet, um eine Textdatei zu TYPE.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>Input: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
