---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: 58cb9e72fc11f0120ed4d99fd5086a195244ac31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233976"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

Konvertieren von Zeichenfolgen in einen Wert mit doppelter Genauigkeit

## <a name="syntax"></a>Syntax

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*-Quelle*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf ein Zeichen, mit dem die Überprüfung beendet wird.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

" **dartod** " gibt den Wert der Gleit Komma Zahl zurück, es sei denn, die Darstellung würde einen Überlauf verursachen. in diesem Fall gibt die Funktion +/-**HUGE_VAL**zurück. Das Vorzeichen des **HUGE_VAL** entspricht dem Vorzeichen des Werts, der nicht dargestellt werden kann. " **Straume** " gibt zurück, `0` Wenn keine Konvertierung ausgeführt werden kann oder ein Unterlauf auftritt.

**wcstod** gibt Werte analog zu " **strantod**" zurück:

- Bei beiden Funktionen wird **errno** auf **ERANGE** festgelegt, wenn ein Überlauf oder ein Unterlauf auftritt.
- Wenn ungültige Parameter vorhanden sind, wird **errno** auf **EINVAL** festgelegt, und der Handler für ungültige Parameter wird aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede Funktion konvertiert die *Eingabe Zeichenfolge* in eine **`double`** . Die " **strautod** "-Funktion konvertiert " *strausource* " in einen Wert mit doppelter Genauigkeit. der Wert von " **stretod** " stoppt das Lesen der Zeichenfolge " *Strauch* " beim ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Dieses Zeichen kann das abschließende Null-Zeichen sein. **wcstod** ist eine breit Zeichen Version von " **strantod**;". Das *unsource* -Argument ist eine Zeichenfolge mit breit Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Die **LC_NUMERIC** Kategorieeinstellung des aktuellen Gebiets Schemas bestimmt die Erkennung des Basispunkt Zeichens in " *strinsource*". Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Funktionen ohne das **_l** -Suffix verwenden das aktuelle Gebiets Schema. **_strtod_l** ist mit **_strtod_l** identisch, außer dass Sie *stattdessen das* übergebene Gebiets Schema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **null**ist, wird ein Zeiger auf das Zeichen, das die Überprüfung beendet hat, an dem Speicherort gespeichert, auf den von *endptr*verwiesen wird. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben), wird der Wert von " *strinsource* " an dem Speicherort gespeichert, auf den von *endptr*verwiesen wird.

der Wert von " **stretod** *" erwartet eine Zeichenfolge mit einer* der folgenden Formen:

[*Leerzeichen*] [*Sign*] {*Ziffern* [*Basis* - *Ziffern*] *&#124; Basis* *Ziffern*} [{**e** &#124; **e**} [*Sign*] *Ziffern*] [*Leerzeichen*] [*Sign*] {**0x** &#124; **0x**} {*Hexziffern* [*Basis* *Hexziffern*] &#124; *Basis* *-Hexziffern*} [{**p** &#124; **p**}*[Sign*] *Hexziffern*] [*Leerzeichen*] [*Sign*] {**INF** &#124; **unendlich**} [*Leerzeichen*] [*Sign*] **NaN** [*Sequence*]

Die optionalen führenden *leer* Zeichen können aus Leerzeichen und Tabstopp Zeichen bestehen, die ignoriert werden. das Vorzeichen ist entweder Pluszeichen (+) oder minus *Zeichen* (-); *Ziffern* sind eine oder mehrere Dezimalstellen. *Hexziffern* sind eine oder mehrere hexadezimale Ziffern. *Basis* ist das Basis-Punktzeichen, entweder ein Punkt (.) im Standard Gebiets Schema "C", oder der Gebiets Schema spezifische Wert, wenn das aktuelle Gebiets Schema anders *ist oder wenn das* Gebiets Schema angegeben ist. eine *Sequenz* ist eine Sequenz von alphanumerischen Zeichen oder Unterstrich Zeichen. In Dezimal-und hexadezimalen Zahlen Formularen, wenn keine Ziffern vor dem Basiszeichen stehen, muss mindestens eine Zeichenfolge nach dem Basispunkt Zeichen angezeigt werden. Im Dezimal Format kann ein Exponent folgen, der aus einem einführenden Buchstaben (**e** oder **e**) und einer optionalen Ganzzahl mit Vorzeichen besteht. Im hexadezimalen Format kann auf die hexadezimalen Ziffern ein Exponent folgen, der aus einem einführenden Buchstaben (**p** oder **p**) und einer optional signierten hexadezimalen Ganzzahl besteht, die den Exponent als Potenz von 2 darstellt. Wenn es in beiden Form keinen Exponententeil oder ein Basiszeichen gibt, wird davon ausgegangen, dass ein Basiszeichen auf die letzte Ziffer in der Zeichenfolge folgt. Die Groß-/Kleinschreibung wird in den **INF** -und **NaN** -Formularen ignoriert. Das erste Zeichen, das nicht in eines dieser Formulare passt, hält den Scanvorgang an.

Die ucrt-Versionen dieser Funktionen unterstützen nicht die Konvertierung von Exponent-Buchstaben vom Fortran-Stil (**d** oder **d**). Diese nicht-standardmäßige Erweiterung wurde in früheren Versionen der CRT unterstützt. Sie ist möglicherweise eine fehlerhafte Änderung für Ihren Code. Die ucrt-Versionen unterstützen hexadezimale Zeichen folgen und Roundtrips von INF-und Nan-Werten, die in früheren Versionen nicht unterstützt wurden. Dies kann auch zu wichtigen Änderungen im Code führen. Beispielsweise würde die Zeichenfolge "0x1A" von " **strautod** " in früheren Versionen als 0,0 interpretiert werden, aber als 26,0 in der ucrt-Version.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|" **strautod**", " **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> oder &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt;stdlib.h> or &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> or &lt;wchar.h> |

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[Funktionen für Zeichen folgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
