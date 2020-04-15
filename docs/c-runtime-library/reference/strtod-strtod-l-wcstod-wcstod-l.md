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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337670"
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

*Strsource*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf ein Zeichen, mit dem die Überprüfung beendet wird.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**strtod** gibt den Wert der Gleitkommazahl zurück, es sei denn, die Darstellung würde einen Überlauf verursachen, in diesem Fall gibt die Funktion +/-**HUGE_VAL**zurück. Das Vorzeichen **HUGE_VAL** entspricht dem Vorzeichen des Werts, der nicht dargestellt werden kann. **strtod** gibt 0 zurück, wenn keine Konvertierung durchgeführt werden kann oder ein Unterlauf auftritt.

**wcstod** gibt Werte analog an **strtod**zurück. Für beide Funktionen wird **errno** auf **ERANGE** gesetzt, wenn ein Über- oder Unterlauf auftritt und der ungültige Parameterhandler aufgerufen wird, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede Funktion konvertiert die Eingabezeichenfolge *strSource* in eine **double**. Die **strtod-Funktion** konvertiert *strSource* in einen Wert mit doppelter Genauigkeit. **strtod** stoppt das Lesen der Zeichenfolge *strSource* beim ersten Zeichen, das es als Teil einer Zahl nicht erkennen kann. Dies ist möglicherweise das beendende NULL-Zeichen. **wcstod** ist eine breitstellige Version von **strtod**; das Argument *strSource* ist eine Zeichenfolge mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Die **LC_NUMERIC** Kategorieeinstellung des aktuellen Gebietsschemas bestimmt die Erkennung des Radixpunktzeichens in *strSource*. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Funktionen ohne **das suffix _l** verwenden das aktuelle Gebietsschema; **_strtod_l** ist identisch mit **_strtod_l** außer dass sie stattdessen das *übergebene Gebietsschema* verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **NULL**ist, wird ein Zeiger auf das Zeichen, das den Scan beendet hat, an der Position gespeichert, auf die *endptr*zeigt. Wenn keine Konvertierung durchgeführt werden kann (es wurden keine gültigen Ziffern gefunden oder eine ungültige Basis angegeben), wird der Wert von *strSource* an der Position gespeichert, auf die *endptr*zeigt.

**strtod** erwartet, dass *strSource* auf eine Zeichenfolge einer der folgenden Formen hinweist:

[*Leerzeichen*] [*Zeichen*] •*Ziffern* [*Radixziffern* *digits*] &#124; *Radixziffern* *digits* **NAN** *sequence***[-e-&#124;** **E**- [*Zeichen*] *Ziffern*] [*Leerzeichen*] [*Zeichen*]**0x** &#124; **0X**-*Hexziffern* [*radix* *hexdigits*] &#124; *radix* *hexdigits*- ['**p** &#124; **P**' [*zeichen*] *hexdigits*] [*whitespace*] [*sign*] '**INF** &#124; **INFINITY**' [*whitespace*] [*sign*

Der optionale führende *Leerraum* kann aus Leerzeichen und Tabstoppzeichen bestehen, die ignoriert werden. *Zeichen* ist entweder plus (+) oder minus (-); *Ziffern* sind eine oder mehrere Dezimalstellen; *Hexziffern* sind eine oder mehrere hexadezimale Ziffern; *radix* ist das Radixpunktzeichen, entweder ein Punkt (.) im Standardgebietsschema "C" oder der gebietsschemaspezifische Wert, wenn das aktuelle Gebietsschema anders ist oder wenn *Gebietsschema* angegeben ist; eine *Sequenz* ist eine Sequenz von alphanumerischen zeichen oder Unterstrichen. Wenn in Dezimal- und Hexadezimalzahlenformen keine Ziffern vor dem Radixpunktzeichen angezeigt werden, muss mindestens eine nach dem Radixpunktzeichen angezeigt werden. In der Dezimalform können die Dezimalstellen durch einen Exponenten gefolgt werden, der aus einem Einführungsbuchstaben (**e** oder **E**) und einer optional signierten Ganzzahl besteht. In der hexadezimalen Form können auf die hexadezimalen Ziffern ein Exponent folgen, der aus einem einführenden Buchstaben (**p** oder **P**) und einer optional signierten hexadezimalen Ganzzahl besteht, die den Exponenten als Macht von 2 darstellt. Wenn in beiden Formen weder ein Exponententeil noch ein Radixpunktzeichen angezeigt wird, wird davon ausgegangen, dass ein Radixpunktzeichen der letzten Ziffer in der Zeichenfolge folgt. Die Anfrage wird sowohl in den **INF-** als auch in der **NAN-Form** ignoriert. Das erste Zeichen, das nicht zu einer dieser Formen passt, stoppt den Scan.

Die UCRT-Versionen dieser Funktionen unterstützen keine Konvertierung von Fortran-Stil (**d** oder **D**) Exponentenbuchstaben. Diese nicht-standardmäßige Erweiterung wurde in früheren Versionen der CRT unterstützt. Sie ist möglicherweise eine fehlerhafte Änderung für Ihren Code. Die UCRT-Versionen unterstützen hexadezimale Zeichenfolgen und das Round-Tripping von INF- und NAN-Werten, die in früheren Versionen nicht unterstützt wurden. Dies kann auch zu Änderungen im Code führen. Beispielsweise würde die Zeichenfolge "0x1a" von **strtod** als 0.0 in früheren Versionen interpretiert, in der UCRT-Version jedoch als 26.0.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> oder &lt;stdlib.h> |
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
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
