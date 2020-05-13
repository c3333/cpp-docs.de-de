---
title: raise
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
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
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 81b92404603820948a384b6ad33421251a27c13c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919551"
---
# <a name="raise"></a>raise

Sendet ein Signal an das ausführende Programm.

> [!NOTE]
> Verwenden Sie diese Methode nicht zum Herunterfahren einer Microsoft Store-App, mit Ausnahme von Test-oder Debugszenarien. Programmgesteuerte oder UI-Methoden zum Schließen einer Store-App sind gemäß den [Microsoft Store Richtlinien](/legal/windows/agreements/store-policies)nicht zulässig. Weitere Informationen finden Sie unter [UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntax

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parameter

*sig*<br/>
Auszulösendes Signal.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt **raise** 0 zurück . Andernfalls gibt es einen Wert ungleich 0 (null) zurück.

## <a name="remarks"></a>Hinweise

Die **raise**-Funktion sendet *sig* an das ausführende Programm. Wenn ein vorheriger Aufruf von **signal** eine Signalverarbeitungsfunktion für *sig* installiert hat, führt **raise** diese Funktion aus. Wenn keine Handlerfunktion installiert wurde, wird die dem Signalwert *sig* zugeordnete Standardaktion wie folgt ausgeführt.

|Signal|Bedeutung|Standard|
|------------|-------------|-------------|
|**SIGABRT**|Nicht ordnungsgemäße Beendigung|Beendet das aufrufende Programm mit Exitcode 3|
|**SIGFPE**|Gleitkommafehler|Beendet das aufrufende Programm|
|**SIGILL**|Ungültige Anweisung|Beendet das aufrufende Programm|
|**SIGINT**|STRG+C-Unterbrechung|Beendet das aufrufende Programm|
|**SIGSEGV**|Ungültiger Speicherzugriff|Beendet das aufrufende Programm|
|**SIGTERM**|An das Programm gesendete Beendigungsanforderung|Ignoriert das Signal|

Wenn das Argument kein gültiges Signal gemäß den oberen Angaben ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn keine Behandlung erfolgt, legt die Funktion **errno** auf **EINVAL** fest und gibt einen Wert ungleich 0 (null) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**__raise**|\<signal.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[Abbruch](abort.md)<br/>
[signal](signal.md)<br/>
