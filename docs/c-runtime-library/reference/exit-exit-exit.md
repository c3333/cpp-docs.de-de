---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347633"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Beendet den aufrufenden Prozess. Die **Exit-Funktion** beendet sie nach dem Bereinigen. **_exit** und **_Exit** sofort beenden.

> [!NOTE]
> Verwenden Sie diese Methode nicht, um eine UWP-App (Universelle Windows-Plattform) herunterzufahren, außer in Test- oder Debugszenarios. Programmgesteuerte oder UI-Möglichkeiten zum Schließen einer Store-App sind gemäß den [Microsoft Store-Richtlinien](/legal/windows/agreements/store-policies)nicht zulässig. Weitere Informationen finden Sie unter [UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle). Weitere Informationen zu Windows 10-Apps finden Sie unter [Anleitungen für Windows 10-Apps](https://developer.microsoft.com/windows/apps).

## <a name="syntax"></a>Syntax

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>Parameter

*Status*<br/>
Beendigungsstatuscode.

## <a name="remarks"></a>Bemerkungen

Die **Funktionen exit**, **_Exit** und **_exit** beenden den Aufrufenprozess. Die **Exit-Funktion** ruft Destruktoren für threadlokale Objekte auf, ruft dann – in LIFO-Reihenfolge (Last-in-First-Out) – die Funktionen auf, die von **atexit** und **_onexit**registriert werden, und löscht dann alle Dateipuffer, bevor sie den Prozess beendet. Die **_Exit-** und **_exit-Funktionen** beenden den Prozess, ohne threadlokale Objekte zu zerstören oder **atexit-** oder **_onexit-Funktionen** zu verarbeiten und ohne Streampuffer zu leeren.

Obwohl **exit**, **_Exit** und **_exit** Aufrufe keinen Wert zurückgeben, wird der *Statuswert* nach dem Beenden des Prozesses für die Hostumgebung oder den wartenden Aufrufprozess verfügbar gemacht, sofern vorhanden. In der Regel legt der Aufrufer den *Statuswert* auf 0 fest, um einen normalen Ausgang oder einen anderen Wert anzuzeigen, um einen Fehler anzuzeigen. Der *Statuswert* ist für den Betriebssystembatchbefehl **ERRORLEVEL** verfügbar und wird durch eine von zwei Konstanten dargestellt: **EXIT_SUCCESS**, die einen Wert von 0 darstellt, oder **EXIT_FAILURE**, der einen Wert von 1 darstellt.

Die Funktionen **exit**, **_Exit**, **_exit**, **quick_exit** **, _cexit**und **_c_exit** verhalten sich wie folgt.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|**Ausfahrt**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**_Exit**|Führt minimale C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**_exit**|Führt minimale C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**quick_exit**|Führt schnelle C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**_cexit**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück. Der Prozess wird nicht beendet.|
|**_c_exit**|Führt minimale C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück. Der Prozess wird nicht beendet.|

Wenn Sie die **Funktion exit** **, _Exit** oder **_exit** aufrufen, werden die Destruktoren für temporäre oder automatische Objekte, die zum Zeitpunkt des Aufrufs vorhanden sind, nicht aufgerufen. Ein automatisches Objekt ist ein nicht statisches lokales Objekt, das in einer Funktion definiert ist. Ein temporäres Objekt ist ein Objekt, das vom Compiler erstellt wird, z. B. ein Wert, der von einem Funktionsaufruf zurückgegeben wird. Um ein automatisches Objekt zu zerstören, bevor Sie **exit**, **_Exit**oder **_exit**aufrufen, rufen Sie explizit den Destruktor für das Objekt auf, wie hier gezeigt:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Verwenden Sie **DLL_PROCESS_ATTACH** nicht, um **Exit** von **DllMain**aufzurufen. Um die **DLLMain-Funktion** zu beenden, geben Sie **FALSE** aus **DLL_PROCESS_ATTACH**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**exit**, **_Exit**, **_exit**|\<process.h> oder \<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[Abbrechen](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
