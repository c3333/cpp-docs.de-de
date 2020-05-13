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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a86b58b868c96b6f77af8bfa32036d1a56b2a7cf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918867"
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

Gibt 0 (null) zurück, wenn erfolgreich, oder-1 im Fall eines Fehlers.

## <a name="remarks"></a>Hinweise

Die **_putenv** -Funktion fügt neue Umgebungsvariablen hinzu oder ändert die Werte vorhandener Umgebungsvariablen. Umgebungsvariablen definieren die Umgebung, in der ein Prozess ausgeführt wird (beispielsweise der Standardsuchpfad für die mit einem Programm zu verknüpfenden Bibliotheken). **_wputenv** ist eine breit Zeichen Version von **_putenv**. Das *envstring* -Argument für **_wputenv** ist eine Zeichenfolge mit breit Zeichen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

Das *envstring* -Argument muss ein Zeiger auf eine Zeichenfolge der Form " *varname*=*value_string*" sein, wobei " *varname* " der Name der hinzu zufügenden oder zu ändernden Umgebungsvariablen und *value_string* der Wert der Variablen ist. Wenn *varname* bereits Teil der Umgebung ist, wird sein Wert durch *value_string*ersetzt; Andernfalls werden die neue *varname* -Variable und Ihr *value_string* Wert der Umgebung hinzugefügt. Sie können eine Variable aus der Umgebung entfernen, indem Sie eine leere *value_string*angeben (oder anders ausgedrückt, indem Sie nur *varname*= angeben).

**_putenv** und **_wputenv** wirken sich nur auf die Umgebung aus, die für den aktuellen Prozess lokal ist. Sie können Sie nicht zum Ändern der Umgebung auf Befehls Ebene verwenden. Das bedeutet, dass diese Funktionen nur bei Datenstrukturen funktionieren, auf die die Laufzeitbibliothek zugreifen kann, aber nicht bei dem Umgebungssegment, das vom Betriebssystem für einen Prozess erstellt wurde. Wenn der aktuelle Prozess beendet wird, wird die Umgebung auf die Ebene des aufrufenden Prozesses zurückgesetzt (in den meisten Fällen die Betriebssystemebene). Die geänderte Umgebung kann jedoch an alle neuen Prozesse geleitet werden, die von **_spawn**, **_exec**oder **System**erstellt werden, und diese neuen Prozesse erhalten alle neuen Elemente, die von **_putenv** und **_wputenv**hinzugefügt werden.

Ändern Sie keinen Umgebungs Eintrag direkt: Verwenden Sie stattdessen **_putenv** oder **_wputenv** , um ihn zu ändern. Insbesondere direkte Freigabe Elemente des globalen Arrays **_environ []** können dazu führen, dass ein ungültiger Speicher adressiert wird.

**getenv** und **_putenv** die globale Variable **_environ** verwenden, um auf die Umgebungs Tabelle zuzugreifen. **_wgetenv** und **_wputenv** **_wenviron**verwenden. **_putenv** und **_wputenv** ändern möglicherweise den Wert von **_environ** und **_wenviron**, wodurch das **_envp** Argument für " **Main** " und das **_wenvp** Argument für " **wmain**" ungültig werden. Daher ist es sicherer, **_environ** oder **_wenviron** zu verwenden, um auf die Umgebungs Informationen zuzugreifen. Weitere Informationen zur Beziehung zwischen **_putenv** und **_wputenv** zu globalen Variablen finden Sie unter [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Die **_putenv** -und **_getenv** Familien von Funktionen sind nicht Thread sicher. **_getenv** könnte einen Zeichen folgen Zeiger zurückgeben, während **_putenv** die Zeichenfolge ändert, was zu zufälligen Fehlern führt. Stellen Sie sicher, dass Aufrufe dieser Funktionen synchronisiert sind.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **_putenv**finden Sie unter [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
