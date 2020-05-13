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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ade4fe613a2fd57df67f58c496b62d7192354654
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918874"
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

*varname*<br/>
Der Umgebungsvariablenname.

*value_string*<br/>
Der Wert, auf den die Umgebungsvariable festgelegt wird.

## <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn erfolgreich, oder einen Fehlercode.

### <a name="error-conditions"></a>Fehlerbedingungen

|*varname*|*value_string*|Rückgabewert|
|------------|-------------|------------------|
|**Normal**|any|**Eingabe**|
|any|**Normal**|**Eingabe**|

Wenn einer dieser Fehlerzustände auftritt, wird ein Handler für ungültige Parameter von diesen Funktionen aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen " **EINVAL** " zurück und legen " **errno** " auf " **EINVAL**" fest.

## <a name="remarks"></a>Hinweise

Die **_putenv_s** -Funktion fügt neue Umgebungsvariablen hinzu oder ändert die Werte vorhandener Umgebungsvariablen. Umgebungsvariablen definieren die Umgebung, in der ein Prozess ausgeführt wird (beispielsweise der Standardsuchpfad für die mit einem Programm zu verknüpfenden Bibliotheken). **_wputenv_s** ist eine breit Zeichen Version von **_putenv_s**. Das *envstring* -Argument für **_wputenv_s** ist eine Zeichenfolge mit breit Zeichen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* ist der Name der Umgebungsvariablen, die hinzugefügt oder geändert werden soll, und *value_string* ist der Wert der Variablen. Wenn *varname* bereits Teil der Umgebung ist, wird sein Wert durch *value_string*ersetzt; Andernfalls werden die neue *varname* -Variable und Ihre *value_string* der Umgebung hinzugefügt. Sie können eine Variable aus der Umgebung entfernen, indem Sie eine leere Zeichenfolge (d. h. "") für *value_string*angeben.

**_putenv_s** und **_wputenv_s** wirken sich nur auf die Umgebung aus, die für den aktuellen Prozess lokal ist. Sie können Sie nicht zum Ändern der Umgebung auf Befehls Ebene verwenden. Diese Funktionen funktionieren nur bei Datenstrukturen, auf die die Laufzeitbibliothek zugreifen kann, aber nicht bei dem Umgebungssegment, das vom Betriebssystem für einen Prozess erstellt wurde. Wenn der aktuelle Prozess beendet wird, wird die Umgebung auf die Ebene des aufrufenden Prozesses zurückgesetzt (in den meisten Fällen die Betriebssystemebene). Die geänderte Umgebung kann jedoch an alle neuen Prozesse geleitet werden, die von **_spawn**, **_exec**oder **System**erstellt werden, und diese neuen Prozesse erhalten alle neuen Elemente, die von **_putenv_s** und **_wputenv_s**hinzugefügt werden.

Einen Umgebungs Eintrag nicht direkt ändern; Verwenden Sie stattdessen **_putenv_s** oder **_wputenv_s** , um Sie zu ändern. Insbesondere das direkte Freigeben von Elementen des globalen Arrays **_environ []** kann dazu führen, dass ein ungültiger Speicher adressiert wird.

**getenv** und **_putenv_s** die globale Variable **_environ** verwenden, um auf die Umgebungs Tabelle zuzugreifen. **_wgetenv** und **_wputenv_s** **_wenviron**verwenden. **_putenv_s** und **_wputenv_s** können den Wert von **_environ** und **_wenviron**ändern und dadurch das Argument "-Argument" für " **Main** " *und das* **_wenvp** Argument für " **wmain**" ungültig machen. Daher ist es sicherer, **_environ** oder **_wenviron** zu verwenden, um auf die Umgebungs Informationen zuzugreifen. Weitere Informationen zur Beziehung zwischen **_putenv_s** und **_wputenv_s** zu globalen Variablen finden Sie unter [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Die **_putenv_s** -und **_getenv_s** Familien von Funktionen sind nicht Thread sicher. **_getenv_s** könnte einen Zeichen folgen Zeiger zurückgeben, während **_putenv_s** die Zeichenfolge ändert, was zu zufälligen Fehlern führen kann. Stellen Sie sicher, dass Aufrufe dieser Funktionen synchronisiert sind.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **_putenv_s**finden Sie unter [getenv_s _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
