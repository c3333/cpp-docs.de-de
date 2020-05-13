---
title: abort
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: f330d53df5af0efa41f4e3b3bb843bdc95210c70
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910902"
---
# <a name="abort"></a>abort

Bricht den aktuellen Prozess ab und gibt einen Fehlercode zurück.

> [!NOTE]
> Verwenden Sie diese Methode nicht zum Herunterfahren Microsoft Store einer APP-oder universelle Windows-Plattform-app (UWP) mit Ausnahme von Test-oder Debugszenarien. Programmgesteuerte oder UI-Methoden zum Schließen einer Store-App sind gemäß den [Microsoft Store Richtlinien](/legal/windows/agreements/store-policies)nicht zulässig. Weitere Informationen finden Sie unter [UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntax

```C
void abort( void );
```

## <a name="return-value"></a>Rückgabewert

**Abbruch** gibt die Steuerung nicht an den aufrufenden Prozess zurück. Standardmäßig sucht es nach einem Abbruchsignalhandler und löst `SIGABRT` aus, sofern vorhanden. Anschließend beendet **Abbruch** den aktuellen Prozess und gibt einen Exitcode an den übergeordneten Prozess zurück.

## <a name="remarks"></a>Hinweise

**Microsoft-spezifisch**

Standardmäßig zeigt die **Abbruch** Routine eine Fehlermeldung an, bevor `SIGABRT` ausgelöst wird, wenn eine APP mit der Debug-Lauf Zeit Bibliothek erstellt wird. Bei Konsolen-Apps, die im Konsolenmodus ausgeführt werden, wird die Meldung an `STDERR` gesendet. Bei Windows-Desktop-Apps und Konsolen-Apps, die im Fenstermodus ausgeführt werden, wird die Meldung in einem Meldungsfeld angezeigt. Zum Unterdrücken der Meldung verwenden Sie [_set_abort_behavior](set-abort-behavior.md), um das `_WRITE_ABORT_MSG`-Flag zu löschen. Die Meldung, die angezeigt wird, hängt von der Version der verwendeten Laufzeitumgebung ab. Bei Anwendungen, die mit den neuesten Versionen von Visual C++ erstellt wurden, sieht die Meldung wie folgt aus:

> R6010-Abort () wurde aufgerufen.

In früheren Versionen der C-Laufzeitbibliothek wurde diese Meldung angezeigt:

> Diese Anwendung hat ein nicht ordnungsgemäßes Beenden der Runtime angefordert. Weitere Informationen erhalten Sie von dem für die Anwendung zuständigen Supportteam.

Wenn das Programm im Debugmodus kompiliert wird, zeigt das Meldungsfeld Optionen zum **Abbrechen**, **Wiederholen** oder **Ignorieren** an. Wenn der Benutzer **Abbrechen** auswählt, wird das Programm sofort beendet und gibt einen Exitcode von 3 zurück. Wenn der Benutzer **Wiederholen** auswählt, wird ein Debugger für Just-In-Time-Debuggen aufgerufen, falls verfügbar. Wenn der Benutzer **ignorieren**auswählt, wird die normale Verarbeitung von **Abbruch** fortgesetzt.

Beim Retail-und Debugbuild prüft **Abbruch** dann, ob ein abbruchsignal Handler festgelegt ist. Wenn ein nicht standardmäßiger Signalhandler festgelegt ist, werden Aufrufe `raise(SIGABRT)` **abgebrochen** . Verwenden Sie die Funktion [Signal](signal.md), um eine Abbruchsignalhandler-Funktion zum `SIGABRT`-Signal zuzuordnen. Sie können benutzerdefinierte Aktionen wie das Bereinigen von Logressourcen oder Loginformationen ausführen und die App mit Ihrem eigenen Fehlercode in der Handlerfunktion beenden. Wenn kein benutzerdefinierter Signalhandler definiert ist, wird das `SIGABRT` Signal von **Abbruch** nicht angehoben.

In nicht Debugbuilds von Desktop-oder Konsolen-apps ruft **Abbruch** standardmäßig den Windows-Fehlerberichterstattung Service-Mechanismus (ehemals Dr. Watson) auf, um Fehler an Microsoft zu melden. Dieses Verhalten kann aktiviert oder deaktiviert werden, indem `_set_abort_behavior` aufgerufen und das `_CALL_REPORTFAULT`-Flag festlegt oder maskiert wird. Wenn das Flag festgelegt ist, zeigt Windows ein Meldungsfeld mit einem Text an, der in etwa wie folgt lautet: Ein Problem hat dazu geführt, dass das Programm gestoppt wurde oder nicht mehr ordnungsgemäß ausgeführt wird. Der Benutzer kann dann entweder einen Debugger über die Schaltfläche **Debuggen** aufrufen oder die Schaltfläche **Programm** schließen auswählen, um die App mit einem vom Betriebssystem definierten Fehlercode beenden.

Wenn der Windows-Fehlerberichts Handler nicht aufgerufen wird, **rufen Sie** auf, [_exit](exit-exit-exit.md) aus, um den Prozess mit Exitcode 3 zu beenden und die Steuerung an den übergeordneten Prozess oder das Betriebssystem zurückgegeben. Von `_exit` werden weder Streampuffer geleert noch eine `atexit`/`_onexit`-Verarbeitung ausgeführt.

Weitere Informationen zum CRT-Debugging finden Sie unter [CRT-Debugverfahren](/visualstudio/debugger/crt-debugging-techniques).

**Microsoft-spezifisch beenden**

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Abbruch**|\<process.h> oder \<stdlib.h>|

## <a name="example"></a>Beispiel

Das folgende Programm versucht, eine Datei zu öffnen und bricht den Vorgang ab, wenn der Versuch fehlschlägt.

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von "abort"](../../cpp/using-abort.md)<br/>
[Abbruch-Funktion](../../c-language/abort-function-c.md)<br/>
[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__raise](raise.md)<br/>
[signal](signal.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
