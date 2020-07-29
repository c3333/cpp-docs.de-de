---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: d99b895076025aa50028bb4cd21df9e13c98197f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233963"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

Konvertiert eine Zeichenfolge in einen Gleitkommawert mit einfacher Genauigkeit.

## <a name="syntax"></a>Syntax

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Parameter

*-Quelle*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf das Zeichen, das die Überprüfung stoppt.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

" **strintof** " gibt den Wert der Gleit Komma Zahl zurück, es sei denn, die Darstellung würde einen Überlauf verursachen. in diesem Fall gibt die Funktion +/-**HUGE_VALF**zurück. Das Vorzeichen des **HUGE_VALF** entspricht dem Vorzeichen des Werts, der nicht dargestellt werden kann. " **strintof** " gibt "0" zurück, wenn keine Konvertierung ausgeführt werden kann oder ein Unterlauf auftritt.

**wcstof** gibt Werte analog zu " **stringron**" zurück. Bei beiden Funktionen wird **errno** auf **ERANGE** festgelegt, wenn ein Überlauf oder ein Unterlauf auftritt, und der Handler für ungültige Parameter wird aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede Funktion konvertiert die *Eingabe Zeichenfolge* in eine **`float`** . Die Funktion " **strintof** " konvertiert " *stresource* " in einen Wert mit einfacher Genauigkeit. " **Straume** " beendet das Lesen der zeichenfolgenzeichenfolge beim ersten Zeichen, das nicht als Teil einer Zahl erkannt werden kann. *strSource* Dies ist möglicherweise das beendende NULL-Zeichen. **wcstof** ist eine breit Zeichen Version von " **strintof**;". Das *unsource* -Argument ist eine Zeichenfolge mit breit Zeichen. Ansonsten verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

Die **LC_NUMERIC** Kategorieeinstellung des aktuellen Gebiets Schemas bestimmt die Erkennung des Basis Zeichens in " *strinsource*". Weitere Informationen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Funktionen, die nicht über das **_l** -Suffix verfügen, verwenden das aktuelle Gebiets Schema. diejenigen mit dem-Suffix sind beinahe identisch, verwenden jedoch stattdessen das übergebene Gebiets Schema. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **null**ist, wird ein Zeiger auf das Zeichen, das die Überprüfung beendet hat, an dem Speicherort gespeichert, auf den von *endptr*verwiesen wird. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben), wird der Wert von " *strinsource* " an dem Speicherort gespeichert, auf den von *endptr*verwiesen wird.

der Wert von " **strintof** " erwartet, dass " *Strauch* " auf eine Zeichenfolge der folgenden Form verweist:

[*Leerzeichen*] [*Sign*] [*Ziffern*] [__.__ *Ziffern*] [{**e** &#124; **e**} [*Sign*] *Ziffern*]

Ein Leerraum kann aus *Leerzeichen und* Tabstopp Zeichen bestehen, die ignoriert werden. das Vorzeichen ist entweder Plus *Zeichen* ( **+** ) oder Minuszeichen ( **-** ), und *Ziffern* sind eine oder mehrere Dezimalstellen. Wenn keine Ziffern vor dem Basiszeichen stehen, muss mindestens eine Ziffer nach dem Basiszeichen stehen. Auf die Dezimalstellen kann ein Exponent folgen, der aus einem einführenden Buchstaben (**e** oder **e**) und einer optionalen Ganzzahl mit Vorzeichen besteht. Wenn weder ein Exponententeil noch ein Basiszeichen angezeigt wird, wird davon ausgegangen, dass ein Basiszeichen auf die letzte Ziffer in der Zeichenfolge folgt. Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung.

Die ucrt-Versionen dieser Funktionen unterstützen nicht die Konvertierung von Exponent-Buchstaben vom Fortran-Stil (**d** oder **d**). Diese nicht-standardmäßige Erweiterung wurde in früheren Versionen der CRT unterstützt. Sie ist möglicherweise eine fehlerhafte Änderung für Ihren Code.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**strtof** **_strtof_l**|C: \<stdlib.h> C++: &lt; cstdlib> oder\<stdlib.h>|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h> oder \<wchar.h> C++: &lt; cstdlib> \<stdlib.h> oder\<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[Funktionen für Zeichen folgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
