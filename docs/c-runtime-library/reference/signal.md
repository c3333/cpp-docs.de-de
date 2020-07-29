---
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 1dacf23b6c4f698b61c5bfe2dd2fb1ff7ee389f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216751"
---
# <a name="signal"></a>signal

Legt die Verarbeitung des Unterbrechungssignals fest.

> [!IMPORTANT]
> Verwenden Sie diese Methode nicht zum Herunterfahren einer Microsoft Store-App, mit Ausnahme von Test-oder Debugszenarien. Programmgesteuerte oder UI-Methoden zum Schließen einer Store-App sind gemäß den [Microsoft Store Richtlinien](/legal/windows/agreements/store-policies)nicht zulässig. Weitere Informationen finden Sie unter [UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntax

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parameter

*Signatur*<br/>
Signalwert.

*func*<br/>
Der zweite Parameter ist ein Zeiger auf die auszuführende Funktion. Der erste Parameter ist ein Signalwert und der zweite Parameter ist ein Untercode, der verwendet werden kann, wenn der erste Parameter SIGFPE lautet.

## <a name="return-value"></a>Rückgabewert

**Signal** gibt den vorherigen Wert von Func zurück, der dem angegebenen Signal zugeordnet ist. Wenn der vorherige Wert von *Func* beispielsweise **SIG_IGN**wurde, wird auch der Rückgabewert **SIG_IGN**. Der Rückgabewert **SIG_ERR** gibt einen Fehler an. in diesem Fall wird **errno** auf **EINVAL**festgelegt.

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **Signal** -Funktion ermöglicht es einem Prozess, eine von mehreren Methoden zum Behandeln eines interruptsignals vom Betriebssystem auszuwählen. Das *sig* -Argument ist die Unterbrechung, auf die das **Signal** antwortet. Es muss eine der folgenden Manifest-Konstanten sein, die in Signal definiert sind. Micha.

|*sig* -Wert|BESCHREIBUNG|
|-----------------|-----------------|
|**SIGABRT**|Nicht ordnungsgemäße Beendigung|
|**SIGFPE**|Gleitkommafehler|
|**SIGILL**|Ungültige Anweisung|
|**SIGINT**|STRG+C-Signal|
|**SIGSEGV**|Ungültiger Speicherzugriff|
|**SIGTERM**|Beendigungsanforderung|

Wenn *sig* keiner der obigen Werte ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validierung](../../c-runtime-library/parameter-validation.md) definiert. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt **SIG_ERR**zurück.

Standardmäßig beendet **Signal** das aufrufende Programm mit Exitcode 3, unabhängig vom Wert von *sig*.

> [!NOTE]
> **SIGINT** wird für Win32-Anwendungen nicht unterstützt. Wenn es zu einer STRG+C-Unterbrechung kommt, generieren Win32-Betriebssysteme einen neuen Thread, um speziell diese Unterbrechung zu verarbeiten. Dies kann dazu führen, dass eine Singlethreadanwendung, z. B. eine Anwendung in UNIX, zu einer Multithreadanwendung wird und ein unerwartetes Verhalten verursacht.

Das *Func* -Argument ist eine Adresse eines von Ihnen geschriebenen Signal Handlers oder einer der vordefinierten Konstanten **SIG_DFL** oder **SIG_IGN**, die auch in Signal definiert werden. Micha. Wenn *Func* eine Funktion ist, wird es als Signalhandler für das angegebene Signal installiert. Der Prototyp des Signal Handlers erfordert ein formales Argument, *sig*, vom Typ **`int`** . Das Betriebssystem stellt das tatsächliche Argument über *sig* bereit, wenn ein Interrupt auftritt. Das-Argument ist das Signal, das die Unterbrechung generiert hat. Daher können Sie die sechs (in der vorangehenden Tabelle aufgeführten) Manifestkonstanten in Ihrem Signalhandler verwenden, um zu bestimmen, welche Unterbrechung aufgetreten ist, und entsprechende Maßnahmen ergreifen. Beispielsweise können Sie **Signal** zweimal aufgerufen werden, um den gleichen Handler zwei verschiedenen Signalen zuzuweisen, und dann das *sig* -Argument im Handler testen, um verschiedene Aktionen auf Grundlage des empfangenen Signals auszuführen.

Wenn Sie Tests für Gleit Komma Ausnahmen (**SIGFPE**) durchlaufen, zeigt *Func* auf eine Funktion, die ein optionales zweites Argument annimmt, das eine von mehreren Manifest-Konstanten ist, die in float definiert sind. H, der Formular **FPE_xxx**. Wenn ein **SIGFPE** -Signal auftritt, können Sie den Wert des zweiten Arguments testen, um die Art der Gleit Komma Ausnahme zu bestimmen und dann die entsprechende Aktion durchführen. Dieses Argument und seine möglichen Werte sind Microsoft-Erweiterungen.

Für Gleit Komma Ausnahmen wird der Wert von *Func* nicht zurückgesetzt, wenn das Signal empfangen wird. Zur Behandlung von Gleitkommaausnahmen verwenden Sie try/except-Klauseln, um die Gleitkommaoperationen zu umschließen. Sie können die Ausnahmen auch beheben, indem Sie [setjmp](setjmp.md) mit [longjmp](longjmp.md) verwenden. In beiden Fällen setzt der aufrufende Prozess die Ausführung fort und lässt den Gleitkommazustand des Prozesses undefiniert.

Wenn der Signalhandler zurückgibt, setzt der aufrufende Prozess die Ausführung sofort fort, und zwar von dem Punkt aus, an dem das Unterbrechungssignal empfangen wurde. Dies gilt unabhängig von der Art des Signals oder des Betriebsmodus.

Bevor die angegebene Funktion ausgeführt wird, wird der Wert von *Func* auf **SIG_DFL**festgelegt. Das nächste Unterbrechungs Signal wird wie für **SIG_DFL**beschrieben behandelt, es sei denn, ein zwischengeschalteter **Signal-Signal** gibt andernfalls an. Sie können diese Funktion verwenden, um Signale in der aufgerufenen Funktion zurückzusetzen.

Da Signalhandlerroutinen im Fall einer Unterbrechung normalerweise asynchron aufgerufen werden, kann Ihre Signalhandlerfunktion möglicherweise die Kontrolle übernehmen, wenn ein Laufzeitvorgang unvollständig ist und einen unbekannten Status aufweist. In der folgenden Liste sind die Einschränkungen zusammengefasst, die bestimmen, welche Funktionen Sie in der Signalhandlerroutine verwenden können.

- Geben Sie auf niedriger Ebene oder stdio nicht aus. H-e/a-Routinen (z. **b. printf** oder **fread**).

- Ruft keine Heap Routinen oder Routinen auf, die die Heap Routinen verwenden (z. b. **malloc**, **_strdup**oder **_putenv**). Weitere Informationen finden Sie unter [malloc](malloc.md).

- Verwenden Sie keine Funktion, die einen Systemaufruf generiert (z. b. **_getcwd** oder **Zeit**).

- Verwenden Sie **longjmp** nicht, es sei denn, der Interrupt wird durch eine Gleit Komma Ausnahme verursacht (d. h. *sig* ist **sigf**). Initialisieren Sie in diesem Fall zuerst das Gleit Komma Paket mithilfe eines Aufrufes **_fpreset**.

- Verwenden Sie keine Overlayroutinen.

Ein Programm muss Gleit Komma Code enthalten, wenn die **SIGFPE** -Ausnahme mithilfe der-Funktion abgefangen werden soll. Wenn Ihr Programm keinen Gleitkommacode enthält und den Signalverarbeitungscode der Laufzeitbibliothek erfordert, deklarieren Sie einfach ein flüchtiges Double und initialisieren Sie es mit Null:

```C
volatile double d = 0.0f;
```

Die Signale **SIGILL** und **SIGTERM** werden unter Windows nicht generiert. Sie sind zur Gewährleistung der ANSI-Kompatibilität enthalten. Daher können Sie Signalhandler für diese Signale mithilfe von **Signal**festlegen, und Sie können diese Signale auch explizit generieren, indem Sie [Raise](raise.md)aufrufen.

Signal Einstellungen werden in erzeugten Prozessen, die durch Aufrufe von [_exec](../../c-runtime-library/exec-wexec-functions.md) -oder [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) -Funktionen erstellt werden, nicht beibehalten. Die Signaleinstellungen werden im neuen Prozess auf die Standardwerte zurückgesetzt.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**signal**|\<signal.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie **Signal** verwendet wird, um dem **SIGABRT** -Signal ein benutzerdefiniertes Verhalten hinzuzufügen. Weitere Informationen zum Abbruchverhalten finden Sie unter [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

Die Ausgabe hängt davon ab, welche Version der Laufzeit verwendet wird, ob es sich bei der App um eine Konsolen-oder Windows-App handelt, und unter Windows-Registrierungs Einstellungen. Für eine Konsolen-APP wird möglicherweise die folgende Meldung an stderr gesendet:

```Output
Debug Error!

Program: c:\Projects\crt_signal\Debug\crt_signal.exe

R6010

- abort() has been called
```

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
