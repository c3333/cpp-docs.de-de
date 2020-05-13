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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a1c0eeaa6d66e91b913ce7940d37409fc4f6ac29
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909676"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Beendet den aufrufenden Prozess. Die **Exit** -Funktion beendet Sie nach der Bereinigung. **_exit** und **_Exit** Sie sofort beenden.

> [!NOTE]
> Verwenden Sie diese Methode nicht zum Herunterfahren einer universelle Windows-Plattform-app (UWP), mit Ausnahme von Test-oder Debugszenarien. Programmgesteuerte oder UI-Methoden zum Schließen einer Store-App sind gemäß den [Microsoft Store Richtlinien](/legal/windows/agreements/store-policies)nicht zulässig. Weitere Informationen finden Sie unter [UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle). Weitere Informationen zu Windows 10-Apps finden Sie unter [Anleitungen für Windows 10-Apps](https://developer.microsoft.com/windows/apps).

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

*status*<br/>
Beendigungsstatuscode.

## <a name="remarks"></a>Hinweise

Die Funktionen **Exit**, **_Exit** und **_exit** beenden den aufrufenden Prozess. Die **Exit** -Funktion ruft Dekonstruktoren für Thread lokale Objekte auf und ruft dann – in LIFO-Reihenfolge (Last-in-First-Out) – die Funktionen auf, die von **atexit** und **_onexit**registriert werden. Anschließend werden alle Datei Puffer geleert, bevor der Prozess beendet wird. Die Funktionen **_Exit** und **_exit** beenden den Prozess, ohne Thread lokale Objekte zu zerstören oder **atexit** -oder **_onexit** Funktionen zu verarbeiten, ohne Streampuffer zu leeren.

Obwohl die Aufrufe **Exit**, **_Exit** und **_exit** keinen Wert zurückgeben, wird der Wert in *Status* der Host Umgebung zur Verfügung gestellt, oder es wird auf den aufrufenden Prozess gewartet, wenn ein solcher vorhanden ist, nachdem der Prozess beendet wurde. Normalerweise legt der Aufrufer den *Status* Wert auf 0 fest, um einen normalen Exit anzugeben, oder auf einen anderen Wert, um einen Fehler anzugeben. Der *Status* Wert ist für den Betriebssystem-Batch Befehl **ERRORLEVEL** verfügbar und wird durch eine von zwei Konstanten dargestellt: **EXIT_SUCCESS**, der einen Wert von 0 darstellt, oder **EXIT_FAILURE**, der den Wert 1 darstellt.

Die Funktionen **Exit**, **_Exit**, **_exit**, **quick_exit**, **_cexit**und **_c_exit** Verhalten sich wie folgt.

|Funktion|Beschreibung|
|--------------|-----------------|
|**exit**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**_Exit**|Führt minimale C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**_exit**|Führt minimale C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**quick_exit**|Führt schnelle C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und übergibt den angegebenen Statuscode der Hostumgebung.|
|**_cexit**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück. Der Prozess wird nicht beendet.|
|**_c_exit**|Führt minimale C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück. Der Prozess wird nicht beendet.|

Wenn Sie die Funktion **Exit**, **_Exit** oder **_exit** aufrufen, werden die Dekonstruktoren für alle temporären oder automatischen Objekte, die zum Zeitpunkt des Aufrufs vorhanden sind, nicht aufgerufen. Ein automatisches Objekt ist ein nicht statisches lokales Objekt, das in einer Funktion definiert ist. Ein temporäres Objekt ist ein Objekt, das vom Compiler erstellt wird, z. b. ein von einem Funktions Aufrufwert zurückgegebener Wert. Zum Zerstören eines automatischen Objekts, bevor Sie **Exit**, **_Exit**oder **_exit**aufzurufen, wird der Dekonstruktor für das Objekt explizit aufgerufen, wie hier gezeigt:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Verwenden Sie **DLL_PROCESS_ATTACH** nicht, um **Exit** from **DllMain**aufzurufen. Wenn Sie die **DllMain** -Funktion beenden möchten, geben Sie **false** aus **DLL_PROCESS_ATTACH**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**Beenden**, **_Exit**, **_exit**|\<process.h> oder \<stdlib.h>|

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

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[Abbruch](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
