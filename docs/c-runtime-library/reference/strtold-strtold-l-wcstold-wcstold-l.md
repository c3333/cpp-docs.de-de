---
title: strtold, _strtold_l, wcstold, _wcstold_l
ms.date: 4/2/2020
api_name:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
- _o__strtold_l
- _o__wcstold_l
- _o_strtold
- _o_wcstold
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: ba57eed25fd8e1310b9e837c55cb1e1f7ec2b718
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912600"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold, _strtold_l, wcstold, _wcstold_l

Konvertiert eine Zeichenfolge in einen Gleitkommawert mit langer doppelter Genauigkeit.

## <a name="syntax"></a>Syntax

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*-Quelle*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf das Zeichen, das die Überprüfung stoppt.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

" **strautold** " gibt den Wert der Gleit Komma Zahl als **Long** **Double**-Wert zurück, außer wenn die Darstellung einen Überlauf verursacht – in diesem Fall gibt die Funktion +/-**HUGE_VALL**zurück. Das Vorzeichen des **HUGE_VALL** entspricht dem Vorzeichen des Werts, der nicht dargestellt werden kann. " **strautold** " gibt "0" zurück, wenn keine Konvertierung ausgeführt werden kann oder ein Unterlauf auftritt.

**wcstold** gibt Werte analog zu " **Strauch**" zurück. Bei beiden Funktionen wird **errno** auf **ERANGE** festgelegt, wenn ein Überlauf oder ein Unterlauf auftritt, und der Handler für ungültige Parameter wird aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Jede Funktion konvertiert die *Eingabe Zeichenfolge* in einen **Long** **Double**-Wert. Die " **strautold** "-Funktion beendet das Lesen der Zeichenfolge " *strinsource* " beim ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Dies ist möglicherweise das beendende NULL-Zeichen. Die breit Zeichen Version von " **Strauch** " ist " **wcstold**". Das *unsource* -Argument ist eine Zeichenfolge mit breit Zeichen. Ansonsten verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Die **LC_NUMERIC** Kategorieeinstellung des aktuellen Gebiets Schemas bestimmt die Erkennung des Basis Zeichens in " *darsource*". Weitere Informationen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Funktionen ohne das **_l** -Suffix verwenden das aktuelle Gebiets Schema. **_strtold_l** und **_wcstold_l** sind identisch mit **_strtold** und **_wcstold** , mit dem Unterschied, dass Sie stattdessen das übergebene Gebiets Schema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **null**ist, wird ein Zeiger auf das Zeichen, das die Überprüfung beendet hat, an dem Speicherort gespeichert, auf den von *endptr*verwiesen wird. Wenn keine Konvertierung ausgeführt werden kann (keine gültigen Ziffern gefunden oder ungültige Basis angegeben), wird der Wert von " *strinsource* " an dem Speicherort gespeichert, auf den von *endptr*verwiesen wird.

" **strautold** " erwartet, dass " *stresource* " auf eine Zeichenfolge der folgenden Form verweist:

[*Leerzeichen*] [*Sign*] [*Ziffern*] [. *Ziffern*] [{**d** &#124; **d** &#124; **e** &#124; **e**} [*Sign*]*Ziffern*]

Ein Leerraum kann aus *Leerzeichen und* Tabstopp Zeichen bestehen, die ignoriert werden. Das *Vorzeichen* ist entweder Plus**+** Zeichen () oder**-** Minuszeichen (); und *Ziffern* sind eine oder mehrere Dezimalstellen. Wenn keine Ziffern vor dem Basiszeichen stehen, muss mindestens eine Ziffer nach dem Basiszeichen stehen. Auf die Dezimalstellen kann ein Exponent folgen, der aus einem einführenden Buchstaben (**d**, **D**, **e** oder **E**) und einer ganzen Zahl mit optionalem Vorzeichen besteht. Wenn weder ein Exponententeil noch ein Basiszeichen angezeigt wird, wird davon ausgegangen, dass ein Basiszeichen auf die letzte Ziffer in der Zeichenfolge folgt. Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtold** **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
