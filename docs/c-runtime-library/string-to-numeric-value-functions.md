---
title: Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: b4936e09de5ee26356b71b66154071a93e252b6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213462"
---
# <a name="string-to-numeric-value-functions"></a>Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Bemerkungen

Jede Funktion in der **strtod**-Familie konvertiert eine mit NULL endende Zeichenfolge in einen numerischen Wert. In der folgenden Tabelle sind die verfügbaren Funktionen aufgeführt.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|`strtod`|Konvertiert eine Zeichenfolge in einen Gleitkommawert mit doppelter Genauigkeit|
|`strtol`|Konvertiert eine Zeichenfolge in eine lange ganze Zahl|
|`strtoul`|Konvertiert eine Zeichenfolge in eine lange ganze Zahl ohne Vorzeichen|
|`_strtoi64`|Konvertieren einer Zeichenfolge in eine 64-Bit- **`__int64`** Ganzzahl|
|`_strtoui64`|Konvertieren einer Zeichenfolge in eine ganze Zahl ohne Vorzeichen (64 Bit) **`__int64`**|

`wcstod`, `wcstol`, `wcstoul` und `_wcstoi64` sind jeweils Breitzeichenversionen von `strtod`, `strtol`, `strtoul` und `_strtoi64`. Das Zeichenfolgenargument für jede dieser Breitzeichenfunktionen ist eine Breitzeichenfolge. Jede Funktion verhält sich genau wie ihre entsprechende Einzelbytezeichen-Version.

Die `strtod`-Funktion akzeptiert zwei Argumente: Das erste ist die Eingabezeichenfolge und das zweite ein Zeiger auf das Zeichen, das den Konvertierungsprozess beendet. `strtol`, `strtoul`, **_strtoi64** und **_strtoui64** akzeptieren ein drittes Argument als Zahlenbasis für die Verwendung im Konvertierungsprozess.

Die Eingabezeichenfolge ist eine Sequenz von Zeichen, die als numerischer Wert des angegebenen Typs interpretiert werden. Jede Funktion stoppt das Lesen der Zeichenfolge beim ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Dies ist möglicherweise das beendende NULL-Zeichen. Für `strtol`, `strtoul`, `_strtoi64` und `_strtoui64` kann dieses beendende Zeichen auch das erste numerische Zeichen größer oder gleich der vom Benutzer angegebenen Zahlenbasis sein.

Wenn der vom Benutzer bereitgestellte Zeiger auf ein Zeichen zum Beenden der Konvertierung beim Aufruf nicht auf **NULL** festgelegt ist, wird an dieser Stelle stattdessen ein Zeiger auf das Zeichen gespeichert, das die Überprüfung beendet hat. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben), wird der Wert des Zeichenfolgenzeigers an dieser Adresse gespeichert.

`strtod` erwartet eine Zeichenfolge im folgenden Format:

[*Leerzeichen*] [*Sign*] [`digits`] [**.**`digits`] [{**d** &#124; **d** &#124; **e** &#124; **e**} [*Sign*] `digits` ]

Ein *whitespace* kann aus Leerzeichen und Tabulatorzeichen bestehen, die ignoriert werden; *sign* ist entweder ein Pluszeichen (**+**) oder ein Minuszeichen (**-**); und `digits` sind eine oder mehrere Dezimalstellen. Wenn keine Ziffern vor dem Basiszeichen stehen, muss mindestens eine Ziffer nach dem Basiszeichen stehen. Auf die Dezimalstellen kann ein Exponent folgen, der aus einem einführenden Buchstaben (**d**, **D**, **e** oder **E**) und einer ganzen Zahl mit optionalem Vorzeichen besteht. Wenn weder ein Exponententeil noch ein Basiszeichen angezeigt wird, wird davon ausgegangen, dass ein Basiszeichen auf die letzte Ziffer in der Zeichenfolge folgt. Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung.

Die Funktionen `strtol`, `strtoul`, `_strtoi64` und `_strtoui64` erwarten eine Zeichenfolge der folgenden Form:

[*Leerzeichen*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [ `digits` ]

Wenn das Basisargument zwischen 2 und 36 liegt, wird dieser Wert als Basis der Zahl verwendet. Wenn es 0 ist, werden die ersten Zeichen, auf die mit dem Zeiger zum Beenden der Konvertierung verwiesen wird, zur Bestimmung der Basis verwendet. Wenn das erste Zeichen 0 und das zweite Zeichen nicht „x“ oder „X“ ist, wird die Zeichenfolge als oktale ganze Zahl interpretiert und andernfalls als Dezimalzahl. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. `strtoul`und `_strtoui64` lassen ein Plus **+** Zeichen () oder minus **-** Zeichen () zu. ein führendes Minuszeichen gibt an, dass der Rückgabewert negiert wird.

Der Ausgabewert ist von der `LC_NUMERIC`-Kategorieneinstellung des Gebietsschemas betroffen; weitere Informationen finden Sie unter [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter.

Wenn der von diesen Funktionen zurückgegebene Wert zu einem Überlauf oder Unterlauf führen würde oder wenn keine Konvertierung möglich ist, werden spezielle Werten zurückgegeben:

|Funktion|Bedingung|Zurückgegebener Wert|
|--------------|---------------|--------------------|
|`strtod`|Überlauf|+/- `HUGE_VAL`|
|`strtod`|Unterlauf oder keine Konvertierung|0|
|`strtol`|+ Überlauf|**LONG_MAX**|
|`strtol`|- Überlauf|**LONG_MIN**|
|`strtol`|Unterlauf oder keine Konvertierung|0|
|`_strtoi64`|+ Überlauf|**_I64_MAX**|
|`_strtoi64`|- Überlauf|**_I64_MIN**|
|`_strtoi64`|Keine Konvertierung|0|
|`_strtoui64`|Überlauf|**_UI64_MAX**|
|`_strtoui64`|Keine Konvertierung|0|

**_I64_MAX**, **_I64_MIN** und **_UI64_MAX** sind in LIMITS.H definiert.

`wcstod`, `wcstol`, `wcstoul`, `_wcstoi64` und `_wcstoui64` sind Breitzeichenversionen von `strtod`, `strtol`, `strtoul`, `_strtoi64` bzw. `_strtoui64`. Der Zeiger auf das Argument zum Beenden der Konvertierung ist für jede dieser Breitzeichenfunktionen eine Breitzeichenfolge. Anderenfalls verhält sich jede dieser Breitzeichenfunktionen genau wie ihre entsprechende Einzelbytezeichen-Version.

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../c-runtime-library/data-conversion.md)<br/>
[Gebietsschema](../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Gleit Komma Unterstützung](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
