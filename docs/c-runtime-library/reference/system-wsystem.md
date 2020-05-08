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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 09353c9cda2bc85d91f57806bc3497e49a19f803
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912391"
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

*-Befehl.*<br/>
Der Befehl, der ausgeführt werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn *Command* **null** ist und der Befehls Interpreter gefunden wird, gibt einen Wert ungleich 0 (null) zurück. Wenn der Befehls Interpreter nicht gefunden wird, gibt 0 zurück und legt **errno** auf **ENOENT**fest. Wenn der *Befehl* nicht **null**ist, gibt **System** den vom Befehls Interpreter zurückgegebenen Wert zurück. Gibt den Wert 0 nur zurück, wenn der Befehlsinterpreter den Wert 0 zurückgibt. Der Rückgabewert-1 weist auf einen Fehler hin, und **errno** wird auf einen der folgenden Werte festgelegt:

|||
|-|-|
| **E2BIG** | Die Argumentliste (systemabhängig) ist zu groß. |
| **ENOENT** | Der Befehlsinterpreter kann nicht gefunden werden. |
| **ENOEXEC** | Die Befehlsinterpreterdatei kann nicht ausgeführt werden, da das Format ungültig ist. |
| **Umomem** | Es ist nicht genügend Arbeitsspeicher verfügbar, um den Befehl auszuführen; der verfügbare Arbeitsspeicher ist beschädigt; oder es ist ein ungültiger Block vorhanden, was darauf hinweist, dass der aufrufende Prozess nicht ordnungsgemäß zugeordnet wurde. |

Weitere Informationen zu diesen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **System** Funktion übergibt den *Befehl* an den Befehls Interpreter, der die Zeichenfolge als Betriebssystem Befehl ausführt. Das **System** verwendet die **COMSPEC** -und **path** -Umgebungsvariablen, um die Befehls Interpreterdatei "cmd. exe" zu suchen. Wenn *command* der Befehl **null**ist, überprüft die Funktion nur, ob der Befehls Interpreter vorhanden ist.

Sie müssen mit [fflush](fflush.md) oder [_flushall](flushall.md)explizit leeren oder einen beliebigen Stream schließen, bevor Sie **System**aufgerufen haben.

**_wsystem** ist eine breit Zeichen Version von **System**. Das *Befehls* Argument für **_wsystem** ist eine Zeichenfolge mit breit Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

In diesem Beispiel wird **System** verwendet, um eine Textdatei einzugeben.

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

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
