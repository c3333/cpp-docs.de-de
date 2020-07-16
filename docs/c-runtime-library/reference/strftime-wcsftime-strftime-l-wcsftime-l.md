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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 57fdd61a966cbeab07c0aeafdad0f6e6fb97cca1
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404319"
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

*der schnellste*<br/>
Ausgabezeichenfolge.

*MaxSize*<br/>
Größe des *schnellsten* Puffers, gemessen in Zeichen (**char** oder **wchar_t**).

*format*<br/>
Formatsteuerzeichenfolge.

*timeptr*<br/>
**TM** -Datenstruktur.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

" **Strauch Zeit** " gibt die Anzahl der Zeichen zurück, die in " *strandest* " platziert werden, und " **WCSF Time** " gibt die entsprechende Anzahl von breit Zeichen

Wenn die Gesamtzahl der Zeichen, einschließlich des abschließenden NULL-Werts, größer als *MaxSize*ist, geben sowohl " **strautime** " als auch " **WCSF Time** " den Wert "0" zurück, und der Inhalt von " *strandest* " ist nicht

Die Anzahl der Zeichen in " *strindest* " ist gleich der Anzahl der Literalzeichen im *Format* sowie aller Zeichen, die dem *Format* über Formatierungscodes hinzugefügt werden können. Das abschließende NULL-Zeichen einer Zeichenfolge wird nicht im Rückgabewert berücksichtigt.

## <a name="remarks"></a>Bemerkungen

Die Funktionen " **strinftime** " und " **wcsftime** " formatieren den **TM** -Zeitwert in *Timeptr* gemäß dem angegebenen *Format* Argument und speichern das Ergebnis *im Puffer.* Maximal werden *MaxSize* -Zeichen in die Zeichenfolge eingefügt. Eine Beschreibung der Felder in der *Timeptr* -Struktur finden Sie unter [Asctime](asctime-wasctime.md). **WCSF Time** ist die breit Zeichen Entsprechung von " **strautime**;". das zugehörige Zeichen folgen Zeiger-Argument verweist auf eine breit Zeichen-Zeichenfolge. Anderenfalls verhalten sich diese Funktionen identisch.

Diese Funktion überprüft ihre Parameter. Wenn *"strindest*", " *Format*" oder " *Timeptr* " ein NULL-Zeiger ist oder wenn die von *Timeptr* adressierte **TM** -Datenstruktur ungültig ist (z. b. Wenn Sie Werte außerhalb des gültigen Bereichs für die Uhrzeit oder das Datum enthält) oder wenn die *Format* Zeichenfolge einen ungültigen Formatierungs Code enthält, wird der [Handler für](../../c-runtime-library/parameter-validation.md)ungültige Parameter aufgerufen, wie Wenn die weitere Ausführung zugelassen wird, gibt die Funktion 0 zurück und legt **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

Das *Format* -Argument besteht aus mindestens einem Code. wie in **printf**wird den Formatierungscodes ein Prozentzeichen () vorangestellt **%** . Zeichen, die nicht mit beginnen, **%** werden unverändert in den *schnellsten*kopiert. Die **LC_TIME** Kategorie des aktuellen Gebiets Schemas wirkt sich auf die Ausgabe Formatierung von " **Strauch Zeit**" aus. (Weitere Informationen zu **LC_TIME**finden Sie unter [setlocale](setlocale-wsetlocale.md).) Die Funktionen " **Strauch Zeit** " und " **WCSF Time** " verwenden das aktuell festgelegte Gebiets Schema. Die **_strftime_l** -und **_wcsftime_l** Versionen dieser Funktionen sind nahezu identisch, verwenden jedoch das Gebiets Schema als Parameter und verwenden diesen anstelle des aktuell festgelegten Gebiets Schemas. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Die Funktionen von " **Strauch Zeit** " unterstützen diese Formatierungscodes:

|||
|-|-|
|Code|Ersetzungszeichenfolge|
|**% a**|Abgekürzte Wochentagsname im Gebiets Schema|
|**% A**|Vollständiger Wochentagsname im Gebiets Schema|
|**% b**|Abgekürzte Monats Name im Gebiets Schema|
|**% B**|Vollständiger Monats Name im Gebiets Schema|
|**% c**|Für das Gebietsschema geeignete Darstellung von Datum und Uhrzeit|
|**% C**|Das Jahr dividiert durch 100 und auf eine ganze Zahl gekürzt, als Dezimalzahl (00 − 99).|
|**% d**|Tag des Monats als Dezimalzahl (01-31)|
|**% D**|Äquivalent zu **% m/% d/% y**|
|**% e**|Tag des Monats als Dezimalzahl (1-31), wobei einzelnen Ziffern ein Leerzeichen vorangestellt wird.|
|**% F**|Äquivalent zu **% Y-% m-% d**|
|**% g**|Die letzten zwei Ziffern des nach ISO 8601 Wochenenden Jahres als Dezimalzahl (00-99).|
|**% G**|Das auf der ISO 8601-Woche basierende Jahr als Dezimalzahl|
|**% h**|Abgekürzte Monats Name (äquivalent zu **% b**)|
|**% H**|Stunde im 24-Stunden-Format (00-23)|
|**% I**|Stunde im 12-Stunden-Format (01-12)|
|**% j**|Tag des Jahres als Dezimalzahl (001-366)|
|**% m**|Monat als Dezimalzahl (01-12)|
|**% M**|Minuten Angabe als Dezimalzahl (00-59)|
|**% n**|Ein Zeilen Trennzeichen (**\n**)|
|**% p**|Das Gebiets Schema "Uhr"/p.m.-Kennung Indikator für 12-Stunden-Uhr|
|**% r**|Die 12-Stunden-Uhrzeit des Gebiets Schemas|
|**% R**|Äquivalent zu **% h:%m**|
|**% S**|Sekunde als Dezimalzahl (00-59)|
|**% t**|Ein horizontales Tabstopp Zeichen (**\t**)|
|**% T**|Entspricht **% h:%m:% S**, dem ISO 8601-Zeitformat|
|**% u**|ISO 8601 Wochentag als Dezimalzahl (1-7; Montag ist 1)|
|**% U**|Wochen Nummer des Jahres als Dezimalzahl (00-53), wobei der erste Sonntag der erste Tag der Woche 1 ist.|
|**% V**|ISO 8601 Wochen Nummer als Dezimalzahl (00-53)|
|**% w**|Weekday als Dezimalzahl (0-6; Sonntag ist 0 (null))|
|**% W**|Wochen Nummer des Jahres als Dezimalzahl (00-53), wobei der erste Montag der erste Tag der Woche 1 ist.|
|**% x**|Datums Darstellung für das Gebiets Schema|
|**% X**|Zeit Darstellung für das Gebiets Schema|
|**% y**|Jahr ohne Jahrhundert als Dezimalzahl (00-99)|
|**% Y**|Jahresangabe mit Jahrhundert als Dezimalzahl|
|**% z**|Der Offset von UTC im ISO 8601-Format; keine Zeichen, wenn Zeitzone unbekannt ist|
|**% Z**|Der Name des Gebiets Schemas oder der Zeit Zonen Abkürzung, abhängig von den Registrierungs Einstellungen. keine Zeichen, wenn Zeitzone unbekannt ist|
|**%%**|Prozentzeichen (%)|

Wie in der **printf** -Funktion kann das- **#** Flag jedem Formatierungs Code als Präfix vorangestellt werden. In diesem Fall wird die Bedeutung des Formatcodes wie folgt geändert.

|Formatcode|Bedeutung|
|-----------------|-------------|
|**% #a**, **% #A**, **% #b**, **% #B**, **% #g**, **% #G**, **% #h**, **% #n**, **% #p**, **% #t**, **% #u**, **% #w**, **% #X**, **% #z**, **% #Z**,**%#%**|**#** das Flag wird ignoriert.|
|**% #c**|Eine lange Datums-und Uhrzeit Darstellung, die für das Gebiets Schema geeignet ist. Beispiel: „Dienstag, 14. März 1995, 12:41:29“.|
|**% #x**|Eine lange Datums Darstellung, die für das Gebiets Schema geeignet ist. Beispiel: „Dienstag, 14. März 1995“.|
|**% #d**, **% #D**, **% #e**, **% #F**, **% #H**, **% #I**, **% #j**, **% #m**, **% #M**, **% #r**, **% #R**, **% #S**, **% #T**, **%**#U, **% #V**, **%**#W, **%**#y, **%** #Y|Entfernen Sie führende Nullen oder Leerzeichen (sofern vorhanden).|

Das von **% V**, **% g**und **% g**erzeugte Jahr 8601 Woche und Wochen basiertes Jahr verwendet eine Woche, die am Montag beginnt, wobei Woche 1 die Woche ist, die den 4. Januar enthält. Dies ist die erste Woche, die mindestens vier Tage im Jahr umfasst. Wenn der erste Montag des Jahres 2., 3. oder 4. ist, sind die vorangehenden Tage Teil der letzten Woche des vorhergehenden Jahres. Für diese Tage wird **% V** durch 53 ersetzt, und sowohl **% g** als auch **% g** werden durch die Ziffern des vorangehenden Jahres ersetzt.

> [!NOTE]
> Bei Verwendung einer der `strftime` Funktionen mit einem `tm` Zeiger, der von zurückgegeben wird `gmtime` , sind die Werte, die über die `%Z` -und- `%z` Spezifizierer gedruckt werden, nicht exakt. Dies liegt daran, dass die `tm` vom C-Standard angegebene Struktur nicht die Informationen für den Zeit Zonen Namen und den Offset enthält. Stattdessen werden die Zeitzoneninformationen über die globalen Variablen [ `_timezone` und `_dstbias` ](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)aufgefüllt.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> oder \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> oder \<wchar.h>|

Die Funktionen **_strftime_l** und **_wcsftime_l** sind Microsoft-spezifisch. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [time](time-time32-time64.md).

## <a name="see-also"></a>Weitere Informationen

[Gebietsschema](../../c-runtime-library/locale.md) <br/>
[Zeitverwaltung](../../c-runtime-library/time-management.md) <br/>
[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
