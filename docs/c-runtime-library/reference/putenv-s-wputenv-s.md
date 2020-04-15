---
title: _putenv_s, _wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: f0164feed05b409ba29ca713f11f4f3323dbaac3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338393"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Erstellt, ändert oder entfernt Umgebungsvariablen. Dies sind Versionen von [_putenv, _wputenv](putenv-wputenv.md), enthalten aber Sicherheitserweiterungen wie unter [Sicherheitserweiterungen im CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>Parameter

*Varname*<br/>
Der Umgebungsvariablenname.

*value_string*<br/>
Der Wert, auf den die Umgebungsvariable festgelegt wird.

## <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn erfolgreich, oder einen Fehlercode.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Varname*|*value_string*|Rückgabewert|
|------------|-------------|------------------|
|**Null**|any|**Einval**|
|any|**Null**|**Einval**|

Wenn einer dieser Fehlerzustände auftritt, wird ein Handler für ungültige Parameter von diesen Funktionen aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **EINVAL** zurück und setzen **errno** auf **EINVAL**.

## <a name="remarks"></a>Bemerkungen

Die **_putenv_s-Funktion** fügt neue Umgebungsvariablen hinzu oder ändert die Werte vorhandener Umgebungsvariablen. Umgebungsvariablen definieren die Umgebung, in der ein Prozess ausgeführt wird (beispielsweise der Standardsuchpfad für die mit einem Programm zu verknüpfenden Bibliotheken). **_wputenv_s** ist eine breit **gefächerte**Version von _putenv_s ; Das *envstring-Argument* für **_wputenv_s** ist eine Zeichenfolge mit großen Zeichen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* ist der Name der Umgebungsvariablen, die hinzugefügt oder geändert werden soll, und *value_string* ist der Wert der Variablen. Wenn *varname* bereits Teil der Umgebung ist, wird sein Wert durch *value_string*ersetzt. Andernfalls werden die neue *varname-Variable* und ihre *value_string* der Umgebung hinzugefügt. Sie können eine Variable aus der Umgebung entfernen, indem Sie eine leere Zeichenfolge (d. h. "") für *value_string*angeben.

**_putenv_s** und **_wputenv_s** wirken sich nur auf die Umgebung aus, die lokal für den aktuellen Prozess ist. Sie können sie nicht verwenden, um die Umgebung auf Befehlsebene zu ändern. Diese Funktionen funktionieren nur bei Datenstrukturen, auf die die Laufzeitbibliothek zugreifen kann, aber nicht bei dem Umgebungssegment, das vom Betriebssystem für einen Prozess erstellt wurde. Wenn der aktuelle Prozess beendet wird, wird die Umgebung auf die Ebene des aufrufenden Prozesses zurückgesetzt (in den meisten Fällen die Betriebssystemebene). Die geänderte Umgebung kann jedoch an alle neuen Prozesse übergeben werden, die von **_spawn**, **_exec**oder **System**erstellt werden, und diese neuen Prozesse erhalten alle neuen Elemente, die von **_putenv_s** und **_wputenv_s**hinzugefügt werden.

Ändern Sie einen Umgebungseintrag nicht direkt; Verwenden Sie **stattdessen _putenv_s** oder **_wputenv_s,** um sie zu ändern. Insbesondere das direkte Freilassen von Elementen des **_environ[]** globalen Arrays kann dazu führen, dass ungültiger Speicher adressiert wird.

**getenv** und **_putenv_s** die globale Variable **_environ** verwenden, um auf die Umgebungstabelle zuzugreifen. **_wgetenv** und **_wputenv_s** **verwenden sie _wenviron**. **_putenv_s** und **_wputenv_s** können den Wert von **_environ** und **_wenviron**ändern und damit das *envp-Argument* in **main** und das **_wenvp-Argument** in **wmain**ungültig machen. Daher ist es sicherer, **_environ** oder **_wenviron** für den Zugriff auf die Umgebungsinformationen zu verwenden. Weitere Informationen zur Beziehung von **_putenv_s** und **_wputenv_s** zu globalen Variablen finden Sie unter [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Die **_putenv_s** und **_getenv_s** Funktionsfamilien sind nicht threadsicher. **_getenv_s** einen Zeichenfolgenzeiger zurückgeben, während **_putenv_s** die Zeichenfolge ändert, und dadurch zufällige Fehler verursachen. Stellen Sie sicher, dass Aufrufe dieser Funktionen synchronisiert sind.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel, das zeigt, wie **_putenv_s**verwendet wird, finden Sie unter [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
