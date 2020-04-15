---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: f3c5631a34c35ed5f5b74e15dfc4225224215b89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365462"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Konvertieren Sie eine Zeichenfolge in einen nicht **signierten __int64** Wert.

## <a name="syntax"></a>Syntax

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Strsource*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf ein Zeichen, mit dem die Überprüfung beendet wird.

*base*<br/>
Zu verwendende Zahlenbasis.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_strtoui64** gibt den in der Zeichenfolge *strSource*dargestellten Wert zurück, es sei denn, die Darstellung würde einen Überlauf verursachen, in diesem Fall gibt sie **_UI64_MAX**zurück. **_strtoui64** gibt 0 zurück, wenn keine Konvertierung durchgeführt werden kann.

**_UI64_MAX** ist in LIMITS definiert. H.

Wenn *strSource* **NULL** oder die *Basis* ungleich Null und entweder kleiner als 2 oder größer als 36 ist, wird **errno** auf **EINVAL**gesetzt.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_strtoui64-Funktion** konvertiert *strSource* in eine **nicht signierte** **__int64**. **_wcstoui64** ist eine breit gefächerte Version von **_strtoui64**; das Argument *strSource* ist eine Zeichenfolge mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Beide Funktionen hören auf, die Zeichenfolge *strSource* beim ersten Zeichen zu lesen, das sie nicht als Teil einer Zahl erkennen können. Dies kann das beendende Nullzeichen sein, oder es kann das erste numerische Zeichen größer oder gleich *Basis*sein.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Die **LC_NUMERIC** Kategorieeinstellung des aktuellen Gebietsschemas bestimmt die Erkennung des Radixzeichens in *strSource*; Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Funktionen ohne das suffix_l verwenden das aktuelle Gebietsschema. **_strtoui64_l** und **_wcstoui64_l** sind identisch mit den entsprechenden Funktionen ohne **das suffix _l,** außer dass sie stattdessen das übergebene Gebietsschema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **NULL**ist, wird ein Zeiger auf das Zeichen, das den Scan beendet hat, an der Position gespeichert, auf die *endptr*zeigt. Wenn keine Konvertierung durchgeführt werden kann (es wurden keine gültigen Ziffern gefunden oder eine ungültige Basis angegeben), wird der Wert von *strSource* an der Position gespeichert, auf die *endptr*zeigt.

**_strtoui64** erwartet, dass *strSource* auf eine Zeichenfolge der folgenden Form hinweist:

> [*Leerzeichen*] [a**+** **-**&#124; ' [**0** [- **x** &#124; **X** ' ]] [*Ziffern* &#124; *Buchstaben*]

Ein *Leerzeichen* kann aus Leerzeichen und Registerkartenzeichen bestehen, die ignoriert werden. *Ziffern* sind eine oder mehrere Dezimalstellen. *Buchstaben* sind einer oder mehrere der Buchstaben "a" bis "z" (oder "A" bis "Z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn *die Basis* zwischen 2 und 36 liegt, wird sie als Basis der Zahl verwendet. Wenn *Base* 0 ist, werden die Anfangszeichen der Zeichenfolge, auf die von *strSource* verwiesen wird, verwendet, um die Basis zu bestimmen. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als ganze Oktalzahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Wenn *basisrist* z. B. 0 ist und das erste gescannte Zeichen '0' ist, wird eine oktale Ganzzahl angenommen, und ein Zeichen '8' oder '9' stoppt den Scan.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> oder \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
