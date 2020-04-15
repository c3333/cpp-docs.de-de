---
title: _putenv, _wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333041"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Erstellt, ändert oder entfernt Umgebungsvariablen. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>Parameter

*envstring*<br/>
Definition der Umgebungszeichenfolge.

## <a name="return-value"></a>Rückgabewert

Gibt 0 zurück, wenn erfolgreich ist, oder -1 im Fehlerfall.

## <a name="remarks"></a>Bemerkungen

Die **_putenv-Funktion** fügt neue Umgebungsvariablen hinzu oder ändert die Werte vorhandener Umgebungsvariablen. Umgebungsvariablen definieren die Umgebung, in der ein Prozess ausgeführt wird (beispielsweise der Standardsuchpfad für die mit einem Programm zu verknüpfenden Bibliotheken). **_wputenv** ist eine breit gefächerte Version von **_putenv**; Das *envstring-Argument* für **_wputenv** ist eine Zeichenfolge mit großen Zeichen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

Das *envstring-Argument* muss ein Zeiger auf eine Zeichenfolge der Form *varname*=*value_string*sein, wobei *varname* der Name der hinzuzufügenden oder zu ändernden Umgebungsvariablen ist und *value_string* der Wert der Variablen ist. Wenn *varname* bereits Teil der Umgebung ist, wird sein Wert durch *value_string*ersetzt. Andernfalls werden die neue *varname-Variable* und ihr *value_string* Wert der Umgebung hinzugefügt. Sie können eine Variable aus der Umgebung entfernen, indem Sie eine leere *value_string*angeben, oder anders gesagt, indem Sie nur *varname*= angeben.

**_putenv** und **_wputenv** nur die Umgebung beeinflussen, die lokal für den aktuellen Prozess ist. Sie können sie nicht verwenden, um die Umgebung auf Befehlsebene zu ändern. Das bedeutet, dass diese Funktionen nur bei Datenstrukturen funktionieren, auf die die Laufzeitbibliothek zugreifen kann, aber nicht bei dem Umgebungssegment, das vom Betriebssystem für einen Prozess erstellt wurde. Wenn der aktuelle Prozess beendet wird, wird die Umgebung auf die Ebene des aufrufenden Prozesses zurückgesetzt (in den meisten Fällen die Betriebssystemebene). Die geänderte Umgebung kann jedoch an alle neuen Prozesse übergeben werden, die von **_spawn**, **_exec**oder **System**erstellt wurden, und diese neuen Prozesse erhalten alle neuen Elemente, die von **_putenv** und **_wputenv**hinzugefügt werden.

Ändern Sie einen Umgebungseintrag nicht direkt, sondern verwenden Sie **_putenv** oder **_wputenv,** um ihn zu ändern. Insbesondere kann das direkte Freilassen von Elementen des **_environ[]** globalen Arrays dazu führen, dass ungültiger Speicher adressiert wird.

**getenv** und **_putenv** die globale Variable **_environ** verwenden, um auf die Umgebungstabelle zuzugreifen. **_wgetenv** und **_wputenv** verwenden **_wenviron**. **_putenv** und **_wputenv** können den Wert von **_environ** und **_wenviron**ändern, wodurch das **_envp-Argument** in **main** und das **_wenvp-Argument** in **wmain**für ungültig erklärt wird. Daher ist es sicherer, **_environ** oder **_wenviron** für den Zugriff auf die Umgebungsinformationen zu verwenden. Weitere Informationen zur Beziehung von **_putenv** und **_wputenv** zu globalen Variablen finden Sie unter [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Die **_putenv** und **_getenv** Funktionsfamilien sind nicht threadsicher. **_getenv** einen Zeichenfolgenzeiger zurückgeben, während **_putenv** die Zeichenfolge ändert, was zu zufälligen Fehlern führt. Stellen Sie sicher, dass Aufrufe dieser Funktionen synchronisiert sind.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Eine Beispielverwendung _putenv **_putenv**finden Sie unter [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
