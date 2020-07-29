---
title: Prozess- und Umgebungssteuerung
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
ms.openlocfilehash: ed8d15181a171b4b6a436a3e410a99b48232bc6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217024"
---
# <a name="process-and-environment-control"></a>Prozess- und Umgebungssteuerung

Verwenden Sie die Prozesssteuerungsroutinen, um Prozesse aus einem Programm heraus zu starten, zu beenden und zu verwalten. Verwenden Sie die Umgebungssteuerungsroutinen, um Informationen zur Betriebssystemumgebung abzurufen und zu ändern.

## <a name="process-and-environment-control-functions"></a>Funktionen der Prozess- und Umgebungssteuerung

|-Routine zurückgegebener Wert|Zweck|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|Bricht einen Prozess ab, ohne Puffer zu leeren oder von **atexit** und **_onexit** registrierte Funktionen aufzurufen.|
|[machung](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Prüft auf Logikfehler.|
|Makros [_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Ähnelt **assert**, ist aber nur in den Debugversionen der Laufzeitbibliotheken verfügbar.|
|[atexit](../c-runtime-library/reference/atexit.md)|Plant Routinen für die Ausführung bei Beendigung des Programms.|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Erstellt einen neuen Thread in einem Windows-Betriebssystemprozess.|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Führt **exit**-Beendigungsverfahren aus (z.B. das Leeren der Puffer) und gibt dann die Steuerung an das aufrufende Programm zurück, ohne den Prozess zu beenden.|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Führt **_exit**-Beendigungsverfahren aus und gibt dann die Steuerung an das aufrufende Programm zurück, ohne den Prozess zu beenden.|
|[_cwait](../c-runtime-library/reference/cwait.md)|Wartet, bis ein anderer Prozess beendet wird.|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Beendet einen Windows-Betriebssystemthread.|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Führt einen neuen Prozess mit einer Argumentliste aus.|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Führt einen neuen Prozess mit einer Argumentliste und einer angegebenen Umgebung aus.|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Führt einen neuen Prozess mithilfe von **PATH**-Variablen und einer Argumentliste aus.|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Führt einen neuen Prozess mit **PATH**-Variablen, einer angegeben Umgebung und einer Argumentliste aus.|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Führt einen neuen Prozess mit einem Argumentarray aus.|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Führt einen neuen Prozess mit einem Argumentarray und einer angegebenen Umgebung aus.|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Führt einen neuen Prozess mithilfe von **PATH**-Variablen und einem Argumentarray aus.|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Führt einen neuen Prozess mit **PATH**-Variablen, einer angegeben Umgebung und einem Argumentarray aus.|
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|Ruft von **atexit** und **_onexit** registrierte Funktionen auf, leert alle Puffer, schließt alle offenen Dateien und beendet den Prozess.|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|Beendet den Prozess sofort, ohne **atexit** oder **_onexit** aufzurufen oder Puffer zu leeren.|
|[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Ruft den Wert der Umgebungsvariablen ab.|
|[_getpid](../c-runtime-library/reference/getpid.md)|Ruft die Prozess-ID-Nummer ab.|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Gespeicherte Stapel Umgebung wiederherstellen; Verwenden Sie es zum Ausführen eines nicht lokalen**`goto`**|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Plant Routinen für die Ausführung bei Beendigung des Programms, wird zur Kompatibilität mit Microsoft C/C++ Version 7.0 und früher verwendet.|
|[_pclose](../c-runtime-library/reference/pclose.md)|Wartet auf einen neuen Befehlsprozessor und schließt den Stream auf der zugeordneten Pipe.|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Druckt eine Fehlermeldung.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Erstellt eine Pipe zum Lesen und Schreiben.|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Erstellt eine Pipe und führt einen Befehl aus.|
|[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Fügt den Wert einer Umgebungsvariablen hinzu oder ändert ihn.|
|[raise](../c-runtime-library/reference/raise.md)|Sendet ein Signal an den aufrufenden Prozess.|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Speichert die Stapel Umgebung. Verwenden Sie, um nicht lokal auszuführen.**`goto`**|
|[signal](../c-runtime-library/reference/signal.md)|Verarbeitet ein Interruptsignal.|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Erstellt einen neuen Prozess mit einer angegebenen Argumentliste und führt ihn aus.|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Erstellt einen neuen Prozess mit einer angegebenen Argumentliste und Umgebung und führt ihn aus.|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Erstellt einen neuen Prozess mithilfe der **PATH**-Variable und angegebenen Argumentliste und führt ihn aus.|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Erstellt einen neuen Prozess mithilfe der **PATH**-Variable, angegebenen Umgebung und Argumentliste und führt ihn aus.|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Erstellt einen neuen Prozess mit einem angegebenen Argumentarray und führt ihn aus.|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Erstellt einen neuen Prozess mit einer angegebenen Umgebung und einem Argumentarray und führt ihn aus.|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Erstellt einen neuen Prozess mithilfe der **PATH**-Variable und dem angegebenen Argumentarray und führt ihn aus.|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Erstellt einen neuen Prozess mithilfe der **PATH**-Variable, der angegebenen Umgebung und dem Argumentarray und führt ihn aus.|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Führt einen Betriebssystembefehl aus.|

Im Windows-Betriebssystem entspricht der erzeugte Prozess dem erzeugenden Prozess. Jeder Prozess kann **_cwait** verwenden, um auf einen Prozess zu warten, dessen Prozess-ID bekannt ist.

Der Unterschied zwischen den Familien **_exec** und **_spawn** ist, dass eine **_spawn**-Funktion die Steuerung vom neuen Prozess an den aufrufenden Prozess zurückgeben kann. In einer **_spawn**-Funktion sind sowohl der aufrufende als auch der neue Prozess im Arbeitsspeicher vorhanden, außer wenn **_P_OVERLAY** angegeben ist. In einer **_exec**-Funktion überlagert der neue Prozess den aufrufenden Prozess, sodass die Steuerung nur dann an den aufrufenden Prozess zurückgegeben werden kann, wenn beim Versuch, die Ausführung des neuen Prozesses zu starten, ein Fehler auftritt.

Zu den Unterschieden zwischen den Funktionen in der **_exec**-Familie ebenso wie zwischen denen der **_spawn**-Familie gehören folgende: die Methode zum Suchen der Datei, die als neuer Prozess ausgeführt werden soll; die Form, in der Argumente an den neuen Prozess übergeben werden; die Methode zum Festlegen der Umgebung. Dies wird in der folgenden Tabelle erläutert. Verwenden Sie eine Funktion, die eine Argumentliste übergibt, wenn die Anzahl von Argumenten konstant oder zur Kompilierzeit bekannt ist. Verwenden Sie eine Funktion, die einen Zeiger auf ein Array mit den Argumenten übergibt, wenn die Anzahl von Argumenten zur Laufzeit ermittelt werden muss. Die Informationen in der folgenden Tabelle gelten auch für die jeweiligen Breitzeichengegenstücke der Funktionen **_spawn** und **_exec**.

### <a name="_spawn-and-_exec-function-families"></a>Funktionsfamilien „_spawn“ und „_exec“

|Functions|PATH-Variable zum Suchen der Datei verwenden|Argumentübergabekonvention|Umgebungseinstellungen|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl**, **_spawnl**|Nein|List|Geerbt vom aufrufenden Prozess|
|**_execle**, **_spawnle**|Nein|List|Zeiger auf Umgebungstabelle für neuen Prozess, der als letztes Argument übergeben wurde|
|**_execlp**, **_spawnlp**|Ja|List|Geerbt vom aufrufenden Prozess|
|**_execvpe**, **_spawnvpe**|Ja|Array|Zeiger auf Umgebungstabelle für neuen Prozess, der als letztes Argument übergeben wurde|
|**_execlpe**, **_spawnlpe**|Ja|List|Zeiger auf Umgebungstabelle für neuen Prozess, der als letztes Argument übergeben wurde|
|**_execv**, **_spawnv**|Nein|Array|Geerbt vom aufrufenden Prozess|
|**_execve**, **_spawnve**|Nein|Array|Zeiger auf Umgebungstabelle für neuen Prozess, der als letztes Argument übergeben wurde|
|**_execvp**, **_spawnvp**|Ja|Array|Geerbt vom aufrufenden Prozess|

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
