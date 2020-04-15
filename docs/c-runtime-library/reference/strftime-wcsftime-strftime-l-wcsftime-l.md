---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350011"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Formatieren einer Zeitzeichenfolge

## <a name="syntax"></a>Syntax

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Strdest*<br/>
Ausgabezeichenfolge.

*Maxsize*<br/>
Größe des *strDest-Puffers,* gemessen in Zeichen (**char** oder **wchar_t**).

*format*<br/>
Formatsteuerzeichenfolge.

*timeptr*<br/>
**tm** tm-Datenstruktur.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**strftime** gibt die Anzahl der zeichen platziert in *strDest* und **wcsftime** gibt die entsprechende Anzahl von breiten Zeichen zurück.

Wenn die Gesamtzahl der Zeichen, einschließlich der beendenden NULL, mehr als *maxsize*ist, geben **sowohl strftime** als auch **wcsftime** 0 und der Inhalt von *strDest* unbestimmt zurück.

Die Anzahl der Zeichen in *strDest* entspricht der Anzahl der Literalzeichen im *Format* sowie allen Zeichen, die über Formatierungscodes zum *Format* hinzugefügt werden können. Das abschließende NULL-Zeichen einer Zeichenfolge wird nicht im Rückgabewert berücksichtigt.

## <a name="remarks"></a>Bemerkungen

Die Funktionen **strftime** und **wcsftime** formatieren den **tm-Zeitwert** in *timeptr* entsprechend dem angegebenen *Formatargument* und speichern das Ergebnis im Puffer *strDest*. Höchstens *werden maxsize* Zeichen in der Zeichenfolge platziert. Eine Beschreibung der Felder in der *Timeptr-Struktur* finden Sie unter [asctime](asctime-wasctime.md). **wcsftime** ist das breitstellige Äquivalent von **strftime**; das Argument string-pointer zeigt auf eine Zeichenfolge mit einem breiten Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Diese Funktion überprüft ihre Parameter. Wenn *strDest*, *format*oder *timeptr* ein Nullzeiger ist oder wenn die von *timeptr* adressierte **tm-Datenstruktur** ungültig ist (z. B. wenn sie Anebenwerte für die Uhrzeit oder das Datum enthält) oder wenn die *Formatzeichenfolge* einen ungültigen Formatierungscode enthält, wird der ungültige Parameterhandler aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion 0 zurück und setzt **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

Das *Formatargument* besteht aus einem oder mehreren Codes. wie in **printf**werden den Formatierungscodes**%** ein Prozentzeichen ( vorangestellt. Zeichen, die nicht **%** mit beginnen, werden unverändert in *strDest*kopiert. Die **LC_TIME** Kategorie des aktuellen Gebietsschemas wirkt sich auf die Ausgabeformatierung von **strftime**aus. (Weitere Informationen **zu LC_TIME**finden Sie unter [setlocale](setlocale-wsetlocale.md).) Die Funktionen **strftime** und **wcsftime** verwenden das aktuell festgelegte Gebietsschema. Die **_strftime_l** und **_wcsftime_l** Versionen dieser Funktionen identisch sind, außer dass sie das Gebietsschema als Parameter verwenden und das anstelle des aktuell festgelegten Gebietsschemas verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Die **strftime-Funktionen** unterstützen diese Formatierungscodes:

|||
|-|-|
|Code|Ersetzungszeichenfolge|
|**%a**|Abgekürzter Wochentagsname im Gebietsschema|
|**%A**|Vollständiger Wochentagsname im Gebietsschema|
|**%b**|Abgekürzter Monatsname im Gebietsschema|
|**%B**|Vollständiger Monatsname im Gebietsschema|
|**%c**|Für das Gebietsschema geeignete Darstellung von Datum und Uhrzeit|
|**%C**|Das Jahr dividiert durch 100 und wird als Dezimalzahl (00-99) auf eine ganze Zahl abgeschnitten.|
|**%d**|Tag des Monats als Dezimalzahl (01 - 31)|
|**%D**|Entspricht **%m/%d/%y**|
|**%e**|Tag des Monats als Dezimalzahl (1 - 31), wobei einzelnen Ziffern ein Leerzeichen vorangestellt wird|
|**%F**|Entspricht **%Y-%m-%d**|
|**%g**|Die letzten 2 Ziffern des Wochenjahres ISO 8601 als Dezimalzahl (00 - 99)|
|**%G**|Das Wochenjahr ISO 8601 als Dezimalzahl|
|**%h**|Abgekürzter Monatsname (entspricht **%b**)|
|**%H**|Stunde im 24-Stunden-Format (00 - 23)|
|**%I**|Stunde im 12-Stunden-Format (01 - 12)|
|**%j**|Tag des Jahres als Dezimalzahl (001 - 366)|
|**%m**|Monat als Dezimalzahl (01 - 12)|
|**%M**|Minute als Dezimalzahl (00 - 59)|
|**%n**|Ein Zeilenumleinenzeichen (**n**)|
|**%p**|A.M./P.M. des Gebietsschemas Indikator für 12-Stunden-Uhr|
|**%r**|Die 12-Stunden-Uhrzeit des Gebietsschemas|
|**%R**|Entspricht **%H:%M**|
|**%S**|Zweite als Dezimalzahl (00 - 59)|
|**%t**|Ein horizontales Tab-Zeichen (**t**)|
|**%T**|Entspricht **%H:%M:%S**, dem ISO 8601-Zeitformat|
|**%u**|ISO 8601 Wochentag als Dezimalzahl (1 - 7; Montag ist 1)|
|**%U**|Wochennummer des Jahres als Dezimalzahl (00 - 53), wobei der erste Sonntag der erste Tag der Woche 1 ist|
|**%V**|ISO 8601 Wochennummer als Dezimalzahl (00 - 53)|
|**%w**|Wochentag als Dezimalzahl (0 - 6; Sonntag ist 0)|
|**%W**|Wochennummer des Jahres als Dezimalzahl (00 - 53), wobei der erste Montag der erste Tag der Woche 1 ist|
|**%x**|Datumsdarstellung für das Gebietsschema|
|**%X**|Zeitdarstellung für das Gebietsschema|
|**%y**|Jahr ohne Jahrhundert, als Dezimalzahl (00 - 99)|
|**%Y**|Jahresangabe mit Jahrhundert als Dezimalzahl|
|**%z**|Der Offset von UTC im ISO 8601-Format; Keine Zeichen, wenn die Zeitzone unbekannt ist|
|**%Z**|Je nach Registrierungseinstellungen entweder der Zeitzonenname oder die Abkürzung der Zeitzone des Gebietsschemas; Keine Zeichen, wenn die Zeitzone unbekannt ist|
|**%%**|Prozentzeichen (%)|

Wie in der **printf-Funktion** kann das **#** Flag jedem Formatierungscode voranstellen. In diesem Fall wird die Bedeutung des Formatcodes wie folgt geändert.

|Formatcode|Bedeutung|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t #u**, **%#w**, **%#X**, %#z , **%#w** **%#Z**, **%#Z****%#%**|**#** Flag wird ignoriert.|
|**%#c**|Lange Datums- und Uhrzeitdarstellung, geeignet für das Gebietsschema. Beispiel: „Dienstag, 14. März 1995, 12:41:29“.|
|**%#x**|Lange Datumsdarstellung, passend zum Gebietsschema. Beispiel: „Dienstag, 14. März 1995“.|
|**%#d**, **%#D**, %#e , **%#F**, **%#H**, **%#I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T**, **%#U**, **%#V**, **%#W**, **%#y**, **%#Y** **%#F**|Entfernen Sie führende Nullen oder Leerzeichen (falls vorhanden).|

Das von **%V**, **%g**und **%G**produzierte Jahr ISO 8601 verwendet eine Woche, die am Montag beginnt, wobei Woche 1 die Woche ist, die den 4. Januar enthält, d. h. die erste Woche, die mindestens vier Tage im Jahr umfasst. Wenn der erste Montag des Jahres der 2., 3. oder 4. ist, sind die vorangegangenen Tage Teil der letzten Woche des Vorjahres. Für diese Tage wird **%V** durch 53 ersetzt, und **%g** und **%G** werden durch die Ziffern des Vorjahres ersetzt.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> oder \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> oder \<wchar.h>|

Die **_strftime_l-** und **_wcsftime_l** Funktionen sind Microsoft-spezifisch. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [time](time-time32-time64.md).

## <a name="see-also"></a>Siehe auch

[Locale](../../c-runtime-library/locale.md) <br/>
[Zeitmanagement](../../c-runtime-library/time-management.md) <br/>
[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
