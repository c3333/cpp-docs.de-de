---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l
ms.date: 4/2/2020
api_name:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
- _o__strtoll_l
- _o__wcstoll_l
- _o_strtoll
- _o_wcstoll
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: d5a0ce8cb2c1d5f88d5439b99047609b32c8d2ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365182"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Konvertiert eine Zeichenfolge in einen **langen** **long-Wert.**

## <a name="syntax"></a>Syntax

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
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
Zeiger auf das Zeichen, das die Überprüfung stoppt.

*base*<br/>
Zu verwendende Zahlenbasis.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**strtoll** gibt den Wert zurück, der in der Zeichenfolge *strSource*dargestellt wird, es sei denn, die Darstellung würde einen Überlauf verursachen – in diesem Fall gibt sie **LLONG_MAX** oder **LLONG_MIN**zurück. Die Funktion gibt 0 zurück, wenn keine Konvertierung ausgeführt werden kann. **wcstoll** gibt Die Werte analog an **strtoll**zurück.

**LLONG_MAX** und **LLONG_MIN** sind in LIMITS definiert. H.

Wenn *strSource* **NULL** oder die *Basis* ungleich Null und entweder kleiner als 2 oder größer als 36 ist, wird **errno** auf **EINVAL**gesetzt.

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **strtoll-Funktion** konvertiert *strSource* in eine **lange** **lange**. Beide Funktionen hören auf, die Zeichenfolge *strSource* beim ersten Zeichen zu lesen, das sie nicht als Teil einer Zahl erkennen können. Dies kann das beendende Nullzeichen sein, oder es kann das erste numerische Zeichen sein, das größer oder gleich *basis*ist. **wcstoll** ist eine breitstellige Version von **strtoll**; das Argument *strSource* ist eine Zeichenfolge mit großen Zeichen. Ansonsten verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Die **LC_NUMERIC** Kategorieeinstellung des Gebietsschemas bestimmt die Erkennung des Radixzeichens in *strSource*; Weitere Informationen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Funktionen, die nicht über das **_l** Suffix verfügen, verwenden das aktuelle Gebietsschema. **_strtoll_l** und **_wcstoll_l** sind identisch mit den entsprechenden Funktionen, die nicht über das Suffix verfügen, mit der Ausnahme, dass sie stattdessen das übergebene Gebietsschema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **NULL**ist, wird ein Zeiger auf das Zeichen, das den Scan beendet hat, an der Position gespeichert, auf die *endptr*zeigt. Wenn keine Konvertierung durchgeführt werden kann (es wurden keine gültigen Ziffern gefunden oder eine ungültige Basis angegeben), wird der Wert von *strSource* an der Position gespeichert, auf die von *endptr*verwiesen wird.

**strtoll** erwartet, dass *strSource* auf eine Zeichenfolge der folgenden Form hinweist:

> [*Leerzeichen*] [a**+** **-**&#124; ' [**0** [- **x** &#124; **X** ' ]] [*Ziffern* &#124; *Buchstaben*]

Ein *Leerzeichen* kann aus Leerzeichen und Registerkartenzeichen bestehen, die ignoriert werden. *Ziffern* sind eine oder mehrere Dezimalstellen; *Buchstaben* sind einer oder mehrere der Buchstaben "a" bis "z" (oder "A" bis "Z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn *die Basis* zwischen 2 und 36 liegt, wird sie als Basis der Zahl verwendet. Wenn *Base* 0 ist, werden die Anfangszeichen der Zeichenfolge, auf die von *strSource* verwiesen wird, verwendet, um die Basis zu bestimmen. Wenn das erste Zeichen "0 " und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als oktale ganze Zahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Wenn z. *B. Basis* 0 ist und das erste gescannte Zeichen '0' ist, wird eine oktale Ganzzahl angenommen und ein Zeichen '8' oder '9' stoppt den Scan.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<stdlib.h>|
|**wcstoll**, **_wcstoll_l**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
